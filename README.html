<!DOCTYPE html>
<html>
<head>
  <title>DSK Cam Viewer</title>
  <style>
    body { font-family: Arial; text-align: center; padding: 20px; }
    video { width: 90%; max-width: 600px; border-radius: 10px; }
  </style>
</head>
<body>
  <h2>DSK Cam Viewer (Penerima)</h2>
  <video id="remoteVideo" autoplay playsinline></video>

  <script>
    const socket = new WebSocket('wss://dsk-cam-relay-server.example.com');
    const vid = document.getElementById('remoteVideo');
    let peerConn = new RTCPeerConnection({
      iceServers: [{ urls: 'stun:stun.l.google.com:19302' }]
    });

    peerConn.ontrack = e => { vid.srcObject = e.streams[0]; };

    peerConn.onicecandidate = e => {
      if (e.candidate) socket.send(JSON.stringify({ type: 'candidate', candidate: e.candidate }));
    };

    socket.onmessage = async (msg) => {
      const data = JSON.parse(msg.data);
      if (data.type === 'offer') {
        await peerConn.setRemoteDescription(new RTCSessionDescription(data.offer));
        const answer = await peerConn.createAnswer();
        await peerConn.setLocalDescription(answer);
        socket.send(JSON.stringify({ type: 'answer', answer }));
      } else if (data.type === 'candidate') {
        await peerConn.addIceCandidate(new RTCIceCandidate(data.candidate));
      }
    };
  </script>
</body>
</html>
