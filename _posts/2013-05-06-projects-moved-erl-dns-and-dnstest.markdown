---
layout: post
title: "Projects Moved: erl-dns and dnstest"
date: 2013-05-06 21:52
comments: true
categories: psa
---
Two projects which I've been spending considerable time on lately, erl-dns and dnstest, have now been moved under the aetrion organization on Github.

## erl-dns

The [erl-dns project](https://github.com/aetrion/erl-dns) is an authoritative DNS server written in Erlang. Warning: don't try this at home.

## dnstest

The [dnstest](https://github.com/aetrion/dnstest) project is a collection of regression tests from the PowerDNS 3 regression test suite which I've switched over to run in an Erlang test harness. I use these tests to test the correctness of the responses from erl-dns.

I'll be writing more about both of these projects in the future, especially as we move erl-dns into production at [DNSimple](https://dnsimple.com).

Update your forks if necessary. Thanks!
