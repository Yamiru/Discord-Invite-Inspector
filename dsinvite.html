<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Discord Invite Inspector</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #2a0845, #6441a5);
      color: #f4f4f4;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding-top: 4rem;
    }

    .container {
      max-width: 720px;
      width: 100%;
      text-align: center;
    }

    .form-control, .btn {
      border-radius: 8px;
    }

    .btn-primary {
      background-color: #7289da;
      border: none;
    }

    .info-card {
      background-color: rgba(0, 0, 0, 0.6);
      border-radius: 1rem;
      padding: 2rem;
      margin-top: 2rem;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.4);
      text-align: left;
      color: #ffffff;
    }

    .description {
      color: #b8b8b8;
      font-style: italic;
    }

    .field {
      margin-bottom: 1rem;
    }

    .field span {
      font-weight: 600;
    }

    .field small {
      color: #d6d6d6;
    }

    .avatar {
      height: 60px;
      width: 60px;
      border-radius: 50%;
      object-fit: cover;
      margin-left: 0.75rem;
    }

    .server-icon {
      height: 64px;
      width: 64px;
      border-radius: 16px;
      object-fit: cover;
      margin-right: 1rem;
    }

    .server-header {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 1rem;
    }

    iframe {
      border-radius: 1rem;
      margin-top: 2rem;
      box-shadow: 0 0 20px rgba(0,0,0,0.5);
    }
  </style>
</head>
<body>

<div class="container">
  <h1 class="mb-4">Discord Invite Inspector</h1>
  <div class="input-group mb-4">
    <input type="text" id="inviteURL" class="form-control" placeholder="Enter Discord invite link or code" />
    <button class="btn btn-primary" onclick="inspectInvite()">Check</button>
  </div>

  <div id="result" style="display: none;">
    <div class="info-card">
      <div class="server-header">
        <img id="serverIcon" class="server-icon" src="" alt="Server Icon" />
        <div>
          <h3 id="serverName" class="mb-0"></h3>
          <p id="guildDescription" class="description mb-0"></p>
        </div>
      </div>

      <div class="field"><span>Invite Code:</span> <small id="inviteCode"></small></div>
      <div class="field"><span>Channel:</span> <small id="channelName"></small></div>
      <div class="field"><span>Created:</span> <small id="serverCreated"></small></div>
      <div class="field"><span>Expires:</span> <small id="inviteExpiration"></small></div>
      <div class="field"><span>Members:</span> <small><span id="membersTotal"></span> total, <span id="membersOnline"></span> online</small></div>
      <div class="field"><span>Boost Level:</span> <small id="boostLevel"></small></div>
      <div class="field"><span>Verification Level:</span> <small id="verificationLevel"></small></div>
      <div class="field d-flex align-items-center"><span>Invited By:</span>
        <img id="inviterAvatar" class="avatar" src="" alt="Inviter">
        <small id="inviterName" class="ms-2"></small>
      </div>
    </div>

    <div id="widgetContainer" class="mt-4"></div>
  </div>
</div>

<script>
function inspectInvite() {
  const input = document.getElementById("inviteURL").value.trim();
  const inviteCode = input.split("/").pop();
  const apiURL = `https://discord.com/api/v10/invites/${inviteCode}?with_counts=true&with_expiration=true`;

  fetch(apiURL)
    .then(res => {
      if (!res.ok) throw new Error("Invalid or expired invite.");
      return res.json();
    })
    .then(data => {
      document.getElementById("result").style.display = "block";

      const g = data.guild || {};
      const c = data.channel || {};
      const inviter = data.inviter || {};
      const iconUrl = g.icon
        ? `https://cdn.discordapp.com/icons/${g.id}/${g.icon}.png`
        : "https://cdn.discordapp.com/embed/avatars/1.png";

      document.getElementById("serverIcon").src = iconUrl;
      document.getElementById("serverName").textContent = g.name || "Unknown Server";
      document.getElementById("guildDescription").textContent = g.description || "No description provided.";
      document.getElementById("inviteCode").textContent = data.code || "-";
      document.getElementById("channelName").textContent = c.name || "-";
      document.getElementById("membersTotal").textContent = data.approximate_member_count ?? "N/A";
      document.getElementById("membersOnline").textContent = data.approximate_presence_count ?? "N/A";
      document.getElementById("boostLevel").textContent = g.premium_tier || "None";
      document.getElementById("verificationLevel").textContent = g.verification_level ?? "-";

      const createdAt = g.id ? new Date(g.id / 4194304 + 1420070400000).toLocaleString() : "-";
      document.getElementById("serverCreated").textContent = createdAt;

      const expiresAt = data.expires_at ? new Date(data.expires_at).toLocaleString() : "Never (Permanent)";
      document.getElementById("inviteExpiration").textContent = expiresAt;

      if (inviter.username) {
        document.getElementById("inviterName").textContent = `${inviter.username}#${inviter.discriminator}`;
        document.getElementById("inviterAvatar").src = `https://cdn.discordapp.com/avatars/${inviter.id}/${inviter.avatar}.png`;
      } else {
        document.getElementById("inviterName").textContent = "Unknown";
        document.getElementById("inviterAvatar").src = "https://cdn.discordapp.com/embed/avatars/0.png";
      }

      if (g.id) {
        fetch(`https://discord.com/api/v10/guilds/${g.id}/widget.json`)
          .then(widgetRes => {
            if (widgetRes.ok) {
              document.getElementById("widgetContainer").innerHTML =
                `<iframe src="https://discord.com/widget?id=${g.id}&theme=dark" width="100%" height="500" allowtransparency="true" frameborder="0" sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"></iframe>`;
            } else {
              document.getElementById("widgetContainer").innerHTML =
                `<p class="text-warning">Widget is disabled or private on this server.</p>`;
            }
          })
          .catch(() => {
            document.getElementById("widgetContainer").innerHTML =
              `<p class="text-warning">Widget could not be loaded.</p>`;
          });
      }
    })
    .catch(error => {
      alert(error.message);
      document.getElementById("result").style.display = "none";
    });
}
</script>

</body>
</html>
