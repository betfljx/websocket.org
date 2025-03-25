touch server.js
nano server.js  # แก้ไขไฟล์
---
title: WebSocket API
description: A reference for the WebSocket API — its events, methods, and properties, alongside usage examples for each of them.
---

# The WebSocket API (WebSockets)

const WebSocket = require('ws');
const express = require('express');

const app = express();
const server = require('http').createServer(app);
const wss = new WebSocket.Server({ server });

wss.on('connection', (ws) => {
    console.log('🔗 Client connected');
    
    ws.on('message', (message) => {
        console.log('📩 Received:', message);
        ws.send(`✅ Server received: ${message}`);
    });

    ws.on('close', () => console.log('❌ Client disconnected'));
});

// API ทดสอบ
app.get('/api/test', (req, res) => {
    res.json({ message: "API ทำงานปกติ" });
});

server.listen(3000, () => {
    console.log('🚀 Server is running on http://localhost:3000');
});
The WebSocket API is an advanced technology that makes it possible to open a two-way interactive communication session between the user's browser and a server. With this API, you can send messages to a server and receive event-driven responses without having to poll the server for a reply.

Note: While a WebSocket connection is functionally somewhat similar to standard Unix-style sockets, they are not related.

## Interfaces

`WebSocket`
The primary interface for connecting to a WebSocket server and then sending and receiving data on the connection.

`CloseEvent`
The event sent by the WebSocket object when the connection closes.

`MessageEvent`
The event sent by the WebSocket object when a message is received from the server.

## Further reading

- Read [about reference](https://diataxis.fr/reference/) in the Diátaxis framework
touch server.js
nano server.js  # แก้ไขไฟล์
const WebSocket = require('ws');
const express = require('express');

const app = express();
const server = require('http').createServer(app);
const wss = new WebSocket.Server({ server });

wss.on('connection', (ws) => {
    console.log('🔗 Client connected');
    
    ws.on('message', (message) => {
        console.log('📩 Received:', message);
        ws.send(`✅ Server received: ${message}`);
    });

    ws.on('close', () => console.log('❌ Client disconnected'));
});

// API ทดสอบ
app.get('/api/test', (req, res) => {
    res.json({ message: "API ทำงานปกติ" });
});

server.listen(3000, () => {
    console.log('🚀 Server is running on http://localhost:3000');
});
