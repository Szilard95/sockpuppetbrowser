![Sock Puppet(eer) Browser](docs/sock-puppet-header.png?raw=true "Sock Puppet(eer) Browser Logo Image")
# Sock Puppet(eer) Browser.

## What is this?

This is a docker image that simply exposes Chrome's CDP protocol (which is what Puppeteer and other 
systems want to connect to - to the outside world via a websocket.

When ever something requiring puppeteer connects via `ws://..` it will spin up a new Chrome browser
instance and connect you through (proxy you through) to that Chrome's DevTools connection.

It also handles throttling, scaling, and accepting extra Chrome settings on the connection query.

Under-the-hood it is a simple Python websockets wrapper using a [puppeteer](https://pptr.dev/) image, so 
that we can be sure that all the basic configuration required for Chrome to work will function well.

## Why do I need this?

This provides a Chrome interface to applications that need it, usually for example as required 
when using Playwright - Playwright will launch a `node` instance and start issuing `CDP` (Chrome protocol)
commands to drive the actual project. So you need this project.

(Playwright gives a high-level command set, which talks to `node`, that `node` then does the low-level CDP
commands to drive Chrome directly)

It is also more efficient to not need that extra `node` process like with some other systems 
(you would end up with two node processes).

### Future ideas

- Some super cool "on the wire" hacks to add custom functionality to CDP, like issuing single commands to download files (PDF) to location https://github.com/dgtlmoon/changedetection.io/issues/2019

Have fun!
