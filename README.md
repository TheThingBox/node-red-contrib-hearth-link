[![License](https://img.shields.io/badge/license-WTFPL-blue.svg)](http://www.wtfpl.net/)
![GitHub issues](https://img.shields.io/github/issues-raw/thethingbox/node-red-contrib-hearth-link.svg)
![GitHub package.json version](https://img.shields.io/github/package-json/v/thethingbox/node-red-contrib-hearth-link.svg)

[![NPM](https://nodei.co/npm/node-red-contrib-hearth-link.png)](https://nodei.co/npm/node-red-contrib-hearth-link/)

![npm](https://img.shields.io/npm/v/node-red-contrib-hearth-link.svg)

# Deprecated

This node is now deprecated, please use [ttb-node-jump](https://github.com/TheThingBox/ttb-node-jump) instead.

### node-red-contrib-hearth-link

node-red-contrib-hearth-link is a Node-RED node to send/receive a msg to/from another device through a common MQTT broker.

# Usage

## heart link in

 <p>It connects to another node type <code>heart link</code>, which can be on another device, and receives its messages.</p>
  <h3>Outputs</h3>
  <ol class="node-ports">
    <li>Standard output
      <dl class="message-properties">
        <dd>the message received from the corresponding node <code>heart link</code>.</dd>
      </dl>
    </li>
  </ol>
  <h3>Details</h3>
  <p>
    The content of <code>msg</code>, sent by another node <code>heart link</code>, from output type, is transmitted when it is received.
    To receive a message, it is necessary that a node <code>heart link</code> with the same link name and with the same key is triggered.
  </p>
  <p>
    The message is deciphered with the <code>AES</code> algorithm using the key as the password.
    The message is received by a subscription to the MQTT broker, defined in the <code>Advanced</code> tab. This MQTT broker must be accessible by both <code>heart link</code> nodes to work.
  </p>
  <p>
    The <code>msg.req</code> and <code>msg.res</code> properties are not preserved.
  </p>

## hearth link out

  <p>It connects to another node <code>heart link</code>, which can be on another device, and sends it the message received as input.</p>
  <h3>Inputs</h3>
  <dl class="message-properties">
    <dt class="optional">topic
      <span class="property-type">string</span>
    </dt>
    <dd>The <code>heart link</code> link name</dd>
    <dt class="optional">key
      <span class="property-type">string</span>
    </dt>
    <dd>The key use to cipher the message.</dd>
  </dl>
  <h3>Details</h3>
  <p>
    The content of <code>msg</code> is sent to another node <code>heart link</code>.
    To send a message, it is necessary that a node <code>heart link</code>, from input type, is set with the same link name and with the same key.
  </p>
  <p>
    The message is chiphered with the <code>AES</code> algorithm using the key as the password.
    The message is sent by a publish on an MQTT broker, defined in the <code>Advanced</code> tab. This MQTT broker must be accessible by both <code>heart link</code> nodes to work.
  </p>
  <p>
    The <code>msg.req</code> and <code>msg.res</code> properties are not preserved.
  </p>
  <h3>Mustache template</h3>
  <p>
    The <code>heart link</code> link name will be rendered with mustache using the <code>msg</code> object if <code>msg.topic</code> does not overwrite it. For sample: if the link name
  </p>
  <pre>{{payload.name}} {{type}} 3</pre>
  <p>
    receives a message containing:
  </p>
  <pre>{<br/>&nbsp;&nbsp;&nbsp;&nbsp;type: 'lamp',<br/>&nbsp;&nbsp;&nbsp;&nbsp;payload: {<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: 'Fred'<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>}</pre>
  <p>
    The link name used will be: <code>Fred lamp 3</code>
  </p>
  <p>
    Note: By default, <code>mustache</code> will escape any HTML entities in the values it substitutes. To prevent this, use <code>{{{triple}}}</code> braces.
  </p>
  <h3>References</h3>
  <ul>
    <li><a href="https://mustache.github.io/mustache.5.html" target="_blank">Mustache</a> - The mustache documentation</li>
  </ul>
