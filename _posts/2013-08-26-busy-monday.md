---
title: Busy Monday
layout: post
created_at: Mon Aug 26 2013 16:09
permalink: /2013-08-26-busy-monday
author: inchworms
twitter: inchworms_
---

Today was a busy day at the Travis CI office. Not only did Sebastian and Gareth make an appearence (they've been out of town over summer), but [Julia](https://twitter.com/juliaguar) and [Carolina](https://twitter.com/carolina) (aka RGSoC [Team D*](http://teamd.postach.io/)) came to work in the office.

We spent the morning looking through our completed Sinatra tests and editing the names of any test descriptions that weren't very clear. In some cases this required reminding ourselves of what the test actually did. Carla earn't herself a 15% More Fun forehead sticker by exploring what **params[:agent]** returned in the test below (it 'captures' the relevant part of the User-Agent header, which in this case is 'World').

	context 'makes captures in user agent pattern available in params[:agent]' do
		let(:app) do
			Sinatra.new do
				user_agent(/Baz (.*)/)
				get('/foo'){'Hello ' + params[:agent].first}
			end
		end

		it "get /foo & HTTP_USER_AGENT = Foo Bar returns correct body" do
			response = get '/foo', {}, {'HTTP_USER_AGENT' => 'Baz World'}
			expect(response.body).to be == "Hello World"
		end
	end

She was happy - especially as she remembered what a 'capture' in a regular expression was. (Matt explained it last week. It's about identifying what the important part to identify is, which you indicate by surrounding with brackets).

![15 % more fun sticker](/inchworms/images/15percentmorefun.jpg)

Work continued into the afternoon.

Then Konstantin returned from his adventures in North America. We were excited to see him and hear about the [french-fry sandwiches](http://images.teamsugar.com/files/upl1/0/6066/06_2009/ddc9df2303ce0fa6_DSC09174.jpg) his colleagues in Pittsburgh fed him.

We also liked his unequivocal praise (naturlich):

<iframe width="360" height="510" src="//www.youtube.com/embed/Y5uFDxv2z-g?rel=0" frameborder="0" allowfullscreen></iframe>

