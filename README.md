<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Pro Dashboard</title>

<!-- Icons -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
body {
  margin: 0;
  font-family: Arial;
  background: #000;
  color: #fff;
}

/* Top */
.top {
  display: flex;
  justify-content: center;
  gap: 10px;
  padding: 10px;
  background: #111;
}

input {
  padding: 8px;
  border-radius: 4px;
  border: none;
}

button {
  padding: 8px 12px;
  border: none;
  cursor: pointer;
}

/* Navbar */
.navbar {
  background: #e0e0e0;
  display: flex;
  justify-content: center;
  position: relative;
}

.nav-item {
  position: relative;
  padding: 12px 20px;
  cursor: pointer;
  font-weight: bold;
}

.nav-item:hover {
  background: #7d3c98;
  color: #fff;
}

/* Mega Menu */
.mega {
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  background: #111;
  display: flex;
  justify-content: center;
  gap: 40px;
  padding: 20px;
  opacity: 0;
  visibility: hidden;
  transform: translateY(10px);
  transition: 0.3s;
}

.nav-item:hover .mega {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}

/* Columns */
.column {
  min-width: 200px;
}

.column h4 {
  color: #aaa;
  margin-bottom: 10px;
  border-bottom: 1px solid #333;
  padding-bottom: 5px;
  font-size: 13px;
}

/* Links */
.column a {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 6px 0;
  color: #fff;
  font-size: 13px;
  text-decoration: none;
  transition: 0.2s;
}

.column a:hover {
  color: #9b59b6;
  transform: translateX(5px);
}

/* Icons */
.column i {
  color: #9b59b6;
}

/* Footer */
.footer {
  text-align: center;
  margin-top: 30px;
  color: #aaa;
}
</style>
</head>

<body>

<!-- Top -->
<div class="top">
  <input id="num1" placeholder="Number With FBB">
  <button onclick="copy('num1')">Copy</button>

  <input id="num2" placeholder="ADSL Number">
  <button onclick="copy('num2')">Copy</button>
</div>

<!-- Navbar -->
<div class="navbar">

  <!-- SALES -->
  <div class="nav-item">SR Sales
    <div class="mega">

      <div class="column">
        <h4>Billing</h4>
        <a href="#"><i class="fa-solid fa-file-invoice"></i> Billing</a>
        <a href="#"><i class="fa-solid fa-money-bill"></i> Payment Methods</a>
        <a href="#"><i class="fa-solid fa-rotate-left"></i> Refund</a>
      </div>

      <div class="column">
        <h4>Offers</h4>
        <a href="#"><i class="fa-solid fa-gift"></i> Valid offers</a>
        <a href="#"><i class="fa-solid fa-clock"></i> Expired offers</a>
        <a href="#"><i class="fa-solid fa-bolt"></i> Extra Quota</a>
      </div>

      <div class="column">
        <h4>Technical</h4>
        <a href="#"><i class="fa-solid fa-wifi"></i> Speed Test</a>
        <a href="#"><i class="fa-solid fa-triangle-exclamation"></i> System Outage</a>
      </div>

      <div class="column">
        <h4>Account</h4>
        <a href="#"><i class="fa-solid fa-user"></i> Username & Password</a>
        <a href="#"><i class="fa-solid fa-gear"></i> Change Data</a>
      </div>

      <div class="column">
        <h4>Support</h4>
        <a href="#"><i class="fa-solid fa-headset"></i> Complaint</a>
        <a href="#"><i class="fa-solid fa-comments"></i> Chat Bot</a>
      </div>

    </div>
  </div>

  <!-- TECH -->
  <div class="nav-item">SR Technical
    <div class="mega">
      <div class="column">
        <h4>Internet</h4>
        <a href="#"><i class="fa-solid fa-wifi"></i> Connection Issue</a>
        <a href="#"><i class="fa-solid fa-router"></i> Router Config</a>
      </div>
    </div>
  </div>

  <!-- MOBILE -->
  <div class="nav-item">Mobile
    <div class="mega">
      <div class="column">
        <h4>Mobile</h4>
        <a href="#"><i class="fa-solid fa-mobile"></i> Recharge</a>
        <a href="#"><i class="fa-solid fa-sim-card"></i> SIM Replacement</a>
      </div>
    </div>
  </div>

</div>

<div class="footer">
  <h3>Ireport / Cases</h3>
</div>

<script>
function copy(id){
  let input = document.getElementById(id);
  input.select();
  document.execCommand("copy");
}
</script>

</body>
</html>import { useState } from "react";
import { Home, LayoutDashboard, Folder, Settings, User } from "lucide-react";

function Page({ title, children }) {
  return (
    <div className="p-6">
      <h1 className="text-3xl font-bold mb-4">{title}</h1>
      {children}
    </div>
  );
}

function Card({ title, value, desc }) {
  return (
    <div className="bg-slate-900 p-5 rounded-2xl border border-slate-800 hover:border-cyan-500 transition">
      <h3 className="text-gray-400 text-sm">{title}</h3>
      <p className="text-2xl font-bold mt-1">{value}</p>
      <p className="text-gray-500 text-sm mt-1">{desc}</p>
    </div>
  );
}

export default function App() {
  const [page, setPage] = useState("home");

  const menu = [
    { id: "home", label: "Home", icon: Home },
    { id: "dashboard", label: "Dashboard", icon: LayoutDashboard },
    { id: "projects", label: "Projects", icon: Folder },
    { id: "profile", label: "Profile", icon: User },
    { id: "settings", label: "Settings", icon: Settings },
  ];

  const renderPage = () => {
    switch (page) {
      case "home":
        return (
          <Page title="Home">
            <div className="grid grid-cols-1 md:grid-cols-3 gap-5">
              <Card title="Users" value="1,240" desc="Active users" />
              <Card title="Projects" value="38" desc="Completed projects" />
              <Card title="Reports" value="12" desc="New reports" />
            </div>
          </Page>
        );

      case "dashboard":
        return (
          <Page title="Dashboard">
            <div className="bg-slate-900 p-6 rounded-2xl border border-slate-800">
              <div className="h-64 flex items-center justify-center text-gray-500">
                📊 Analytics Dashboard (Chart area ready)
              </div>
            </div>
          </Page>
        );

      case "projects":
        return (
          <Page title="Projects">
            <div className="grid md:grid-cols-2 gap-4">
              {["Website UI", "Mobile App", "Admin Panel", "API System"].map((p) => (
                <div key={p} className="p-5 bg-slate-900 rounded-2xl border border-slate-800 hover:border-cyan-500 transition">
                  <h4 className="text-lg font-bold">{p}</h4>
                  <p className="text-gray-400 text-sm">Professional project module</p>
                </div>
              ))}
            </div>
          </Page>
        );

      case "profile":
        return (
          <Page title="Profile">
            <div className="bg-slate-900 p-6 rounded-2xl border border-slate-800">
              <p className="text-gray-400">Name: User</p>
              <p className="text-gray-400">Role: Developer</p>
              <p className="text-gray-400">Status: Active</p>
            </div>
          </Page>
        );

      case "settings":
        return (
          <Page title="Settings">
            <div className="bg-slate-900 p-6 rounded-2xl border border-slate-800">
              <p className="text-gray-400">Theme settings</p>
              <p className="text-gray-400">Account settings</p>
              <p className="text-gray-400">Security settings</p>
            </div>
          </Page>
        );

      default:
        return null;
    }
  };

  return (
    <div className="flex h-screen bg-slate-950 text-white">
      {/* Sidebar */}
      <div className="w-64 bg-slate-900 p-5 border-r border-slate-800">
        <h1 className="text-2xl font-bold text-cyan-400 mb-8">System UI</h1>

        <div className="space-y-2">
          {menu.map((item) => {
            const Icon = item.icon;
            return (
              <button
                key={item.id}
                onClick={() => setPage(item.id)}
                className={`flex items-center gap-3 w-full p-3 rounded-xl transition hover:bg-cyan-500/20 ${page === item.id ? "bg-cyan-500/20 text-cyan-400" : "text-gray-300"}`}
              >
                <Icon size={18} />
                {item.label}
              </button>
            );
          })}
        </div>
      </div>

      {/* Main */}
      <div className="flex-1 overflow-auto">
        <div className="p-6 border-b border-slate-800 flex justify-between">
          <h2 className="text-xl font-bold">Professional System</h2>
          <button className="bg-cyan-500 text-black px-4 py-2 rounded-xl font-bold">
            + Create
          </button>
        </div>

        {renderPage()}
      </div>
    </div>
  );
}
