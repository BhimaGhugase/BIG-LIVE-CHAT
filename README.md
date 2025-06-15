Client (Web & Mobile)
  |
  |---> Auth Service
  |---> Messaging Gateway (Socket.IO/WebRTC)
  |---> API Gateway (REST APIs)
  |---> Location Service
  |
Backend (Node.js/NestJS or Django)
  |
  |---> User Management
  |---> Chat Engine
  |---> Video Call Signaling
  |---> Geo Services
  |---> Database
Users (
  id, name, email, phone, profilePic, status, location
)

Messages (
  id, senderId, receiverId, content, timestamp, type (text/image/video)
)

Chats (
  id, participants[], lastMessage, updatedAt
)

Calls (
  id, callerId, receiverId, type (voice/video), startTime, endTime, status
)

Locations (
  userId, latitude, longitude, updatedAt
)

Nearby (
  userId, nearbyUsers[]
)


---// Socket.IO - sample server
io.on('connection', (socket) => {
  socket.on('join', (userId) => socket.join(userId));
  socket.on('send_message', ({to, message}) => {
    io.to(to).emit('receive_message', message);
  });
});
navigator.geolocation.watchPosition((pos) => {
  socket.emit('share_location', {
    lat: pos.coords.latitude,
    lng: pos.coords.longitude
  });
});/login

/chat

/video-call

/map

/profile/big-live-chat/
├── backend/
│   └── server.js (Express/NestJS)
│   └── routes/, controllers/, models/
├── frontend-web/
│   └── React App
├── mobile-app/
│   └── React Native App
└── README.md
