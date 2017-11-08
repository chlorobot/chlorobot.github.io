---
layout: post
title:  "Understanding and Controlling Relays with a Raspberry Pi"
date: Wed Nov 8 00:10:57 EST 2017
categories: raspberry pi relay wiring
---

As a kid I was so excited for 'garage-sailing' with my dad - no not searching for used
<a href="https://www.youtube.com/watch?v=yyYhZ9HH8cI">Christopher Cross</a> albums - but to buy whatever electronic
garbage I could disassemble; assuming I could convince the old man to pony up the shrapnel. Items like 8-track, cassette and
record players, answering machines, whatever had a motor or something interesting to an 8 year old like:

* DC Motors
* LEDs
* Potentiometers
* Shiny things

At one point I came across a computer printer at the side of the road, naturally I took it home
to learn what's inside - to my chagrin all I found were alien devices with way more wires than I was
used to.

### Now in my 30's...

More than two wires is still confusing to me, despite the 14+ years programming and system engineering -
electrical engineering is Greek or Chinese or something that I've absolutely no idea about.

### Get to the point, IDC about that

Relays have two states :

* Usually on
* Usually off

Relays have three leads :
* Normally Open (NO)
* Normally Closed (NC)
* Common (COM)

These are represnted like :

												   L       LL
	This side is mostly disconnected all the time  |______/ |  This side is usually connected.
	                                               NO   COM NC

You have two options :

* Apply power to the relay controller to turn a thing **off** that is usually **on**
* Apply power to the relay controller to turn a thing **on** that is usually **off**

Consider the circuit in the diagram above : if you were to apply electricity to the leftmost and center leads your device
would be in a default 'off' state.

If you were to apply electricity to the rightmost and center leads your device would be in a default 'on' state.

So three wires aren't that scary anymore.


### How the Raspberry Pi handles this stuff

<img src="/images/fulls/relay.jpg" class="fit image" />
<em>Here's a single module relay to simplify the idea</em>

On the relay controller side (the side opposite the wire screws for a single module relay) you'll find three pins.

VCC and GND should look pretty familiar, apply 5v to the VCC and GND pin on the Pi to the GND on the relay and you're set.

But then there's this other pin - wtf does that do? The answer is simple - connect it to any GPIO pin on your Pi ond
pull it 'high' - see what happens, pull it 'low' and see what happens -- this has been documented a million times before
but here's a code snippet anyway :

	PIN = 23 # this should be the GPIO pin you connected the relay to
	import RPi.GPIO as GPIO
	GPIO.setmode(GPIO.BCM)
    GPIO.setup(PIN, GPIO.OUT)
    GPIO.output(PIN, GPIO.HIGH)

	GPIO.output(PIN, GPIO.LOW) # This will either close your 'NO` or open your `NC` of your relay - depending on yoru wiring

I'm getting tired, feel free to email <a mailto="hello@chlorobot.com">me</a> if you get stuck.
