---
title: Berlin map
layout: post
created_at: Thu Aug 22 2013 17:00
permalink: /blog/2013-08-22-berlin-map
author: inchworms
twitter: inchworms_
---

There are more than just a programming issue when you want to draw a map with d3. It took literally half a day to find a working Berlin map. 

<img src="/images/not_working_json.png" alt="berlin" style="width: 600px;"/>
**Not working json**
<p></p>
Then I came across that [github account](https://github.com/m-hoerz/berlin-shapes) with a perfectly working map with the districs already in geojson format. Just what I was looking for.

<img src="/images/working_json.png" alt="berlin" style="width: 600px;"/>
**working json**

Isn't it gorgeous? And look at the colors!
Anyway then I made a choropleth map out of it and finally (took me half a day and a movie-evening with friend(there were complaing I wasn't watching)) got bars that are transforming from the BOTTOM to the top like normal bars do and not from the top to bottom. <s>And the number of the population that are supposed to be on every bar is not there, although its on my localhost, argggggg! Just imagine they are there.</s>Resolved. Thanks to Matt!

<div id="geo_mapping_berlin" style="height: 650px;" ></div>

<script type="text/javascript">
(function() {
      var w = 800;
      var h = 650;

        //Create SVG element
      var svg = d3.select("#geo_mapping_berlin")
            .append("svg")
            .attr("width", w)
            .attr("height", h);

      var color = d3.scale.quantize()
                .range(["rgb(255,247,188)","rgb(254,227,145)","rgb(254,196,79)","rgb(254,153,41)","rgb(236,112,20)","rgb(204,76,2)","rgb(153,52,4)","rgb(102,37,6)"]);

      d3.csv("/data/berlin_population.csv", function(data) {

        var yScale = d3.scale.linear()
          .domain([d3.min(data, function(d) { return d.population; }), d3.max(data, function(d) { return d.population; }) ])
          .range([20, h/3.5]);
          // console.log(yScale(2))

        //Set input domain for color scale
        color.domain([
          d3.min(data, function(d) { return d.population; }), 
          d3.max(data, function(d) { return d.population; })
        ]);

        d3.json("/data/berlin.json", function(json) {
          //Merge the ag. data and GeoJSON
          //Loop through once for each ag. data value
          for (var i = 0; i < data.length; i++) {

            //Grab state name
            var dataDistrict = data[i].district;

            //Grab data value, and convert from string to float
            var dataPopulation = parseFloat(data[i].population);
            var dataLat = parseFloat(data[i].lat);
            var dataLon = parseFloat(data[i].lon);
        
            //Find the corresponding state inside the GeoJSON
            for (var j = 0; j < json.features.length; j++) {
              var jsonDistrict = json.features[j].properties.Name;
              if (dataDistrict == jsonDistrict) {
                //Copy the data Population into the JSON
                json.features[j].properties.population = dataPopulation;
                json.features[j].properties.lat = dataLat;
                json.features[j].properties.lon = dataLon;

                //Stop looking through the JSON
                break;
                }
              }
            }

          var center = d3.geo.centroid(json);
          
          //Tooltip div added
          var div_tooltip = d3.select("body").append("div")
            .attr("class", "tooltip")
            .style("opacity", 0);



          //Define map projection
          var projection = d3.geo.mercator()
                .center(center)
                .scale([350000])
                .translate([w/2, h/2]);


          //Define path generator
          var path = d3.geo.path()
                   .projection(projection);


          svg.selectAll("path")
            .data(json.features)
            .enter()
            .append("path")
            .attr("d", path)
            .style("stroke", 'white')
            .style("stroke-width", 2)
            .style("fill", function(d) {
              //Get data value
              var population = d.properties.population;
              
              if (population) {
                //If value exists…
                return color(population);
              } else {
                //If value is undefined…
                return "#ccc";
              }
            })
            .on("mouseover", function(d) {
              d3.select(this).style("stroke", "white").style("stroke-width", 5)
              div_tooltip
                .transition()
                .duration(200)
                .style("opacity", .9);
              div_tooltip
                .html("<b>" + d.properties.Name + "</b></br> Population:" + d.properties.population)
                .style("left", (d3.event.pageX) + "px")
                .style("top", (d3.event.pageY - 28) + "px");
              number
                .text(d.properties.population)
                .attr("x", function() {
                  return (projection([d.properties.lon, d.properties.lat])[0]) + "px";
                  })
                .attr("y", function() {
                  return (projection([d.properties.lon, d.properties.lat])[1]) + "px";
                  })
              number
                .transition()
                .duration(600)
                .attr("x", function() {
                  return (projection([d.properties.lon, d.properties.lat])[0]) + "px";
                  })
                .attr("y", function() {
                  return (projection([d.properties.lon, d.properties.lat])[1]) - yScale(d.properties.population) - 1 + "px";
                  });
              rectangle
                .attr("x", function() {
                  return (projection([d.properties.lon, d.properties.lat])[0]);
                  })
                .attr("y", function() {
                  return (projection([d.properties.lon, d.properties.lat])[1])
                  });
              rectangle
                .attr("height", 0)
                .transition()
                .duration(600)
                .attr("height", function() {
                  return yScale(d.properties.population);
                  })
                .attr("y", function() {
                  return (projection([d.properties.lon, d.properties.lat])[1]) - yScale(d.properties.population);
                  })
                })
            .on("mouseout", function(d) {
              div_tooltip
                .transition()
                .duration(500)
                .style("opacity", 0);
              d3.select(this)
                .style("stroke", "white")
                .style("stroke-width", 2);
              });

          var rectangle = svg.append("rect")
                .attr("width", 70)
                .style("fill", "#06665D")
                .style("opacity", 0.9);

          var number = d3.select("svg").append("text")
            .attr("class", "number");
          });
        });

      // //Width and height
      // var w = 800;
      // var h = 550;

      // //Create SVG element
      // var svg = d3.select("#geo_mapping_berlin")
      //       .append("svg")
      //       .attr("width", w)
      //       .attr("height", h);

      // var color = d3.scale.quantize()
      //           .range(["rgb(255,247,188)","rgb(254,227,145)","rgb(254,196,79)","rgb(254,153,41)","rgb(236,112,20)","rgb(204,76,2)","rgb(153,52,4)","rgb(102,37,6)"]);

      // d3.csv("/data/berlin_population.csv", function(data) {

      //   var yScale = d3.scale.linear()
      //     .domain([d3.min(data, function(d) { return d.population; }), d3.max(data, function(d) { return d.population; }) ])
      //     .range([20, h/3.5]);
      //     // console.log(yScale(2))

      //   //Set input domain for color scale
      //   color.domain([
      //     d3.min(data, function(d) { return d.population; }), 
      //     d3.max(data, function(d) { return d.population; })
      //   ]);

      //   d3.json("/data/berlin.json", function(json) {
      //     //Merge the ag. data and GeoJSON
      //     //Loop through once for each ag. data value
      //     for (var i = 0; i < data.length; i++) {
        
      //       //Grab state name
      //       var dataDistrict = data[i].district;
            
      //       //Grab data value, and convert from string to float
      //       var dataPopulation = parseFloat(data[i].population);
      //       var dataLat = parseFloat(data[i].lat);
      //       var dataLon = parseFloat(data[i].lon);
        
      //       //Find the corresponding state inside the GeoJSON
      //       for (var j = 0; j < json.features.length; j++) {
            
      //         var jsonDistrict = json.features[j].properties.Name;
        
      //         if (dataDistrict == jsonDistrict) {
            
      //           //Copy the data Population into the JSON
      //           json.features[j].properties.population = dataPopulation;
      //           json.features[j].properties.lat = dataLat;
      //           json.features[j].properties.lon = dataLon;

                
      //           //Stop looking through the JSON
      //           break;
                
      //           }
      //         }
      //       }

      //     var center = d3.geo.centroid(json);
          
      //     //Tooltip div added
      //     var div_tooltip = d3.select("body").append("div")
      //       .attr("class", "tooltip_geomapping")
      //       .style("opacity", 0);



      //     //Define map projection
      //     var projection = d3.geo.mercator()
      //           .center(center)
      //           .scale([350000])
      //           .translate([w/2, h/2]);


      //     //Define path generator
      //     var path = d3.geo.path()
      //              .projection(projection);


      //     svg.selectAll("path")
      //       .data(json.features)
      //       .enter()
      //       .append("path")
      //       .attr("d", path)
      //       .style("stroke", 'white')
      //       .style("stroke-width", 2)
      //       .style("fill", function(d) {
      //         //Get data value
      //         var population = d.properties.population;
              
      //         if (population) {
      //           //If value exists…
      //           return color(population);
      //         } else {
      //           //If value is undefined…
      //           return "#ccc";
      //         }
      //       })
      //       .on("mouseover", function(d) {
      //         d3.select(this).style("stroke", "white").style("stroke-width", 5)
      //         div_tooltip
      //           .transition()
      //           .duration(200)
      //           .style("opacity", .9);
      //         div_tooltip
      //           .html("<strong>" + d.properties.Name + "</strong></br> Population:" + d.properties.population)
      //           .style("left", (d3.event.pageX) + "px")
      //           .style("top", (d3.event.pageY - 28) + "px");
      //         div_number
      //           .text(d.properties.population)
      //           .style("left", function() {
      //             return (projection([d.properties.lon, d.properties.lat])[0]) + "px";
      //             })
      //           .style("top", function() {
      //             return (projection([d.properties.lon, d.properties.lat])[1]) -180 + "px";
      //             })
      //         div_number
      //           .style("top", h)
      //           .transition()
      //           .duration(600)
      //           .style("left", function() {
      //             return (projection([d.properties.lon, d.properties.lat])[0]) + "px";
      //             })
      //           .style("top", function() {
      //             return (projection([d.properties.lon, d.properties.lat])[1]) - yScale(d.properties.population) - 18 + "px";
      //             });
      //         rectangle
      //           .attr("x", function() {
      //             // console.log("x=" + (projection([d.properties.lon, d.properties.lat])[0]))
      //             return (projection([d.properties.lon, d.properties.lat])[0]);
      //             })
      //           .attr("y", function() {
      //             console.log("y vor transition=" + (projection([d.properties.lon, d.properties.lat])[1]))
      //             console.log("y nach transition"+ ((projection([d.properties.lon, d.properties.lat])[1]) - yScale(d.properties.population)))
      //             console.log("yScale oder height =" + yScale(d.properties.population))
      //             return (projection([d.properties.lon, d.properties.lat])[1])
      //             });
      //         rectangle
      //           .attr("height", 0)
      //           .transition()
      //           .duration(600)
      //           .attr("height", function() {
      //             return yScale(d.properties.population);
      //             })
      //           .attr("y", function() {
      //             return (projection([d.properties.lon, d.properties.lat])[1]) - yScale(d.properties.population);
      //             })
      //           })
      //       .on("mouseout", function(d) {
      //         div_tooltip
      //           .transition()
      //           .duration(500)
      //           .style("opacity", 0);
      //         d3.select(this)
      //           .style("stroke", "white")
      //           .style("stroke-width", 2);
      //         });

      //     var rectangle = svg.append("rect")
      //           .attr("width", 70)
      //           .style("fill", "#06665D")
      //           .style("opacity", 0.9);

      //     var div_number = d3.select("svg").append("div")
      //       .attr("class", "number")
      //       .style("fill", "black");
      //     });
      //   });

  })()
</script>




