import { useState } from "react";
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
