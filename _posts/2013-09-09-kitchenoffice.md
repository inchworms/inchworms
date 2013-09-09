---
title: Kitchen Office
layout: post
created_at: Mon Sep 09 2013 15:00
permalink: /blog/2013-09-09-kitchenoffice
author: inchworms
twitter: inchworms_
---

Today we had to do a lot of things: plan what we would work on in the last few weeks of RGSoC, start thinking about our presentation at RubyShift later in the month, bake a special cake for Travis (more on that tomorrow), and add a new table to our database. All in Anja's kitchen.

![kitchenoffice](/images/kitchenoffice.jpg)

We wrote a new migration:

    Sequel.migration do
      change do
        create_table(:payment_year_totals) do
          primary_key :id
          BigDecimal :amount_euro
          foreign_key(:year_id, :years)
          foreign_key(:recipient_id, :recipients)
        end
      end
    end

and a rake task:

    task :run_any_new_migration do
        require "sequel"
        Sequel.extension :migration

        DB = Sequel.postgres("farmsubsidy_performance")
        Sequel::Migrator.run(DB, './db/migrations', :use_transactions=>true)
    end

and ruby code to populate it:

    require 'rubygems'
    require 'sequel'
    require 'logger'


    # connect to an in-memory database
    DB = Sequel.postgres("farmsubsidy_performance", :loggers => [Logger.new($stdout)])

    # connect to the models
    project_root = File.dirname(File.absolute_path(__FILE__))
    Dir.glob(project_root + "/models/*.rb").each{|f| require f}

    # connect to payments total table and add data to the database
    total_payment = DB[:payment_year_totals]

    # look through all recipients and all years and insert the total amount
    Recipient.all.each do |recipient|
      Year.all.each do |year|
        total = recipient.total_payment_amount_by_year(year.year)
        #make sure the total isn't 0
        if total != 0.0
          total_payment.insert(
            recipient_id: recipient.id,
            year_id: year.id,
            amount_euro: total
            )
        end
      end
    end

...and now we have a new database with all the recipients and the total payments per recipient per year.

    farmsubsidy_performance=# SELECT count(*) from payment_year_totals;
    count 
    -------
    5775
    (1 row)

We also discussed the recent election in Australia, and its [political system](http://en.wikipedia.org/wiki/Parliament_of_Australia) vs the [German system](http://en.wikipedia.org/wiki/Politics_of_Germany). The German one seems to be slightly more difficult.

![australia_government](/images/government.jpg)

Anyway the winner of the election in Australia is:

![abbott](/images/abbottbeach.jpg)

