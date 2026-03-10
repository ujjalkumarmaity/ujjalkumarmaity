

<!--
**ujjalkumarmaity/ujjalkumarmaity** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

import { useState, useEffect } from "react";

const repos = [
  { name: "neural-forge", lang: "Python", color: "#3572A5", stars: 4821, forks: 912, desc: "High-performance deep learning toolkit built on JAX", updated: "2d ago", topic: ["ml", "jax", "deep-learning"] },
  { name: "voxel-engine", lang: "Rust", color: "#dea584", stars: 3204, forks: 487, desc: "Real-time voxel rendering engine with procedural generation", updated: "5d ago", topic: ["gamedev", "rendering", "wasm"] },
  { name: "chroma-ui", lang: "TypeScript", color: "#3178c6", stars: 2891, forks: 341, desc: "Accessible component library with zero runtime dependencies", updated: "1d ago", topic: ["react", "components", "a11y"] },
  { name: "pathfinder-cli", lang: "Go", color: "#00ADD8", stars: 1567, forks: 203, desc: "Blazing fast code navigator and semantic search for any codebase", updated: "1w ago", topic: ["cli", "search", "developer-tools"] },
  { name: "hypersync", lang: "Rust", color: "#dea584", stars: 987, forks: 134, desc: "Zero-copy data synchronization protocol over WebTransport", updated: "3d ago", topic: ["networking", "protocol", "performance"] },
  { name: "eigenflow", lang: "Python", color: "#3572A5", stars: 723, forks: 98, desc: "Automatic differentiation engine with symbolic math backend", updated: "2w ago", topic: ["autodiff", "math", "research"] },
];

const contributions = [
  [0,1,2,1,0,2,3,4,3,2,1,2,3,4,4,3,2,1,2,3],
  [1,2,3,4,3,2,1,0,1,2,3,4,4,3,4,3,2,3,4,4],
  [2,3,4,4,3,2,1,2,3,4,3,2,1,2,3,4,3,4,3,2],
  [0,1,2,3,4,3,4,3,2,1,0,1,2,3,4,3,2,1,2,3],
  [1,2,3,2,1,2,3,4,3,2,1,2,3,4,4,3,2,3,4,3],
  [3,4,4,3,2,1,2,3,4,3,2,3,4,3,2,1,2,3,4,4],
  [2,3,4,3,2,3,4,3,2,1,2,3,4,4,3,2,1,2,3,2],
];

function StarIcon() {
  return (
    <svg width="14" height="14" viewBox="0 0 16 16" fill="currentColor">
      <path d="M8 .25a.75.75 0 01.673.418l1.882 3.815 4.21.612a.75.75 0 01.416 1.279l-3.046 2.97.719 4.192a.75.75 0 01-1.088.791L8 12.347l-3.766 1.98a.75.75 0 01-1.088-.79l.72-4.194L.818 6.374a.75.75 0 01.416-1.28l4.21-.611L7.327.668A.75.75 0 018 .25z"/>
    </svg>
  );
}

function ForkIcon() {
  return (
    <svg width="14" height="14" viewBox="0 0 16 16" fill="currentColor">
      <path d="M5 3.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm0 2.122a2.25 2.25 0 10-1.5 0v.878A2.25 2.25 0 005.75 8.5h1.5v2.128a2.251 2.251 0 101.5 0V8.5h1.5a2.25 2.25 0 002.25-2.25v-.878a2.25 2.25 0 10-1.5 0v.878a.75.75 0 01-.75.75h-4.5A.75.75 0 015 6.25v-.878zm3.75 7.378a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm3-8.75a.75.75 0 11-1.5 0 .75.75 0 011.5 0z"/>
    </svg>
  );
}

function RepoCard({ repo, index }) {
  const [hovered, setHovered] = useState(false);
  return (
    <div
      onMouseEnter={() => setHovered(true)}
      onMouseLeave={() => setHovered(false)}
      style={{
        background: hovered ? "rgba(255,255,255,0.06)" : "rgba(255,255,255,0.03)",
        border: `1px solid ${hovered ? "rgba(255,255,255,0.15)" : "rgba(255,255,255,0.07)"}`,
        borderRadius: "12px",
        padding: "20px",
        cursor: "pointer",
        transition: "all 0.25s ease",
        transform: hovered ? "translateY(-2px)" : "translateY(0)",
        boxShadow: hovered ? "0 8px 32px rgba(0,0,0,0.3)" : "none",
        animation: `fadeIn 0.4s ease ${index * 0.07}s both`,
      }}
    >
      <div style={{ display: "flex", alignItems: "flex-start", justifyContent: "space-between", marginBottom: "8px" }}>
        <div style={{ display: "flex", alignItems: "center", gap: "8px" }}>
          <svg width="14" height="14" viewBox="0 0 16 16" fill="#8b949e">
            <path d="M2 2.5A2.5 2.5 0 014.5 0h8.75a.75.75 0 01.75.75v12.5a.75.75 0 01-.75.75h-2.5a.75.75 0 110-1.5h1.75v-2h-8a1 1 0 00-.714 1.7.75.75 0 01-1.072 1.05A2.495 2.495 0 012 11.5v-9zm10.5-1V9h-8c-.356 0-.694.074-1 .208V2.5a1 1 0 011-1h8z"/>
          </svg>
          <span style={{ color: "#58a6ff", fontFamily: "'DM Mono', monospace", fontSize: "14px", fontWeight: 600 }}>{repo.name}</span>
        </div>
        <span style={{ fontSize: "11px", color: "#8b949e", fontFamily: "'DM Mono', monospace" }}>{repo.updated}</span>
      </div>
      <p style={{ color: "#8b949e", fontSize: "13px", margin: "0 0 14px", lineHeight: 1.5, fontFamily: "'Sora', sans-serif" }}>{repo.desc}</p>
      <div style={{ display: "flex", gap: "8px", flexWrap: "wrap", marginBottom: "14px" }}>
        {repo.topic.map(t => (
          <span key={t} style={{ background: "rgba(88,166,255,0.1)", color: "#58a6ff", fontSize: "11px", padding: "2px 8px", borderRadius: "20px", fontFamily: "'DM Mono', monospace" }}>#{t}</span>
        ))}
      </div>
      <div style={{ display: "flex", gap: "16px", alignItems: "center" }}>
        <span style={{ display: "flex", alignItems: "center", gap: "4px" }}>
          <span style={{ width: "10px", height: "10px", borderRadius: "50%", background: repo.color, display: "inline-block" }}/>
          <span style={{ color: "#8b949e", fontSize: "12px", fontFamily: "'DM Mono', monospace" }}>{repo.lang}</span>
        </span>
        <span style={{ display: "flex", alignItems: "center", gap: "4px", color: "#8b949e", fontSize: "12px" }}>
          <StarIcon/>{repo.stars.toLocaleString()}
        </span>
        <span style={{ display: "flex", alignItems: "center", gap: "4px", color: "#8b949e", fontSize: "12px" }}>
          <ForkIcon/>{repo.forks.toLocaleString()}
        </span>
      </div>
    </div>
  );
}

export default function GitHubProfile() {
  const [activeTab, setActiveTab] = useState("repos");
  const [tooltip, setTooltip] = useState(null);

  const intensityColor = (v) => {
    if (v === 0) return "rgba(255,255,255,0.05)";
    if (v === 1) return "#0e4429";
    if (v === 2) return "#006d32";
    if (v === 3) return "#26a641";
    return "#39d353";
  };

  const totalStars = repos.reduce((a, r) => a + r.stars, 0);
  const totalForks = repos.reduce((a, r) => a + r.forks, 0);

  return (
    <div style={{
      minHeight: "100vh",
      background: "#0d1117",
      fontFamily: "'Sora', sans-serif",
      color: "#e6edf3",
      padding: "0",
    }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Sora:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap');
        @keyframes fadeIn { from { opacity:0; transform: translateY(12px) } to { opacity:1; transform: translateY(0) } }
        @keyframes pulse { 0%,100% { opacity:1 } 50% { opacity:0.5 } }
        * { box-sizing: border-box; margin: 0; padding: 0; }
        ::-webkit-scrollbar { width: 6px; } ::-webkit-scrollbar-track { background: #0d1117; } ::-webkit-scrollbar-thumb { background: #30363d; border-radius: 3px; }
        .tab-btn { background: none; border: none; cursor: pointer; padding: 12px 4px; font-family: 'Sora', sans-serif; font-size: 14px; border-bottom: 2px solid transparent; transition: all 0.2s; }
        .tab-btn:hover { color: #e6edf3 !important; }
        .stat-chip:hover { background: rgba(255,255,255,0.08) !important; }
      `}</style>

      {/* Header Banner */}
      <div style={{ height: "120px", background: "linear-gradient(135deg, #0a192f 0%, #1a2744 40%, #0f3d2e 100%)", position: "relative", overflow: "hidden" }}>
        {[...Array(20)].map((_, i) => (
          <div key={i} style={{
            position: "absolute",
            width: Math.random() * 2 + 1 + "px", height: Math.random() * 2 + 1 + "px",
            background: "rgba(255,255,255,0.4)", borderRadius: "50%",
            left: (i * 5.2) + "%", top: Math.random() * 100 + "%",
            animation: `pulse ${2 + Math.random() * 3}s ease infinite ${Math.random() * 2}s`,
          }}/>
        ))}
      </div>

      <div style={{ maxWidth: "900px", margin: "0 auto", padding: "0 24px 60px" }}>
        {/* Avatar Row */}
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-end", marginBottom: "16px" }}>
          <div style={{ marginTop: "-48px", position: "relative" }}>
            <div style={{
              width: "100px", height: "100px", borderRadius: "50%",
              background: "linear-gradient(135deg, #1a6b3c, #1a4a7a)",
              border: "4px solid #0d1117",
              display: "flex", alignItems: "center", justifyContent: "center",
              fontSize: "38px", fontWeight: 700, color: "#fff",
              animation: "fadeIn 0.5s ease both",
            }}>AK</div>
            <div style={{
              position: "absolute", bottom: "6px", right: "6px",
              width: "14px", height: "14px", borderRadius: "50%",
              background: "#3fb950", border: "2px solid #0d1117",
            }}/>
          </div>
          <button style={{
            background: "rgba(255,255,255,0.06)", border: "1px solid rgba(255,255,255,0.15)",
            color: "#e6edf3", padding: "8px 18px", borderRadius: "8px",
            cursor: "pointer", fontSize: "13px", fontFamily: "'Sora', sans-serif",
            fontWeight: 500, transition: "all 0.2s",
          }}>✏️ Edit profile</button>
        </div>

        {/* Bio */}
        <div style={{ animation: "fadeIn 0.5s ease 0.1s both" }}>
          <h1 style={{ fontSize: "24px", fontWeight: 700, marginBottom: "4px", letterSpacing: "-0.5px" }}>Alex Kim</h1>
          <p style={{ color: "#8b949e", fontSize: "16px", marginBottom: "12px", fontWeight: 400 }}>@alexkimdev</p>
          <p style={{ color: "#c9d1d9", fontSize: "14px", lineHeight: 1.6, marginBottom: "16px", maxWidth: "480px" }}>
            Building systems that think. Open-source toolsmith. I write Rust & Python. Previously @ DeepMind, now crafting my own chaos.
          </p>
          <div style={{ display: "flex", flexWrap: "wrap", gap: "14px", color: "#8b949e", fontSize: "13px", marginBottom: "20px" }}>
            {[
              { icon: "🏢", text: "Freelance / Open Source" },
              { icon: "📍", text: "San Francisco, CA" },
              { icon: "🔗", text: "alexkim.dev" },
              { icon: "🕐", text: "Joined March 2016" },
            ].map(item => (
              <span key={item.text} style={{ display: "flex", alignItems: "center", gap: "5px" }}>
                {item.icon} {item.text}
              </span>
            ))}
          </div>

          {/* Stats Row */}
          <div style={{ display: "flex", gap: "20px", marginBottom: "24px", flexWrap: "wrap" }}>
            {[
              { label: "followers", value: "2.4k" },
              { label: "following", value: "318" },
              { label: "total stars", value: totalStars.toLocaleString() },
              { label: "total forks", value: totalForks.toLocaleString() },
            ].map(s => (
              <span key={s.label} className="stat-chip" style={{
                display: "flex", gap: "6px", alignItems: "center",
                padding: "6px 12px", borderRadius: "8px", cursor: "pointer",
                background: "rgba(255,255,255,0.04)", border: "1px solid rgba(255,255,255,0.07)",
                transition: "all 0.2s",
              }}>
                <span style={{ color: "#e6edf3", fontWeight: 600, fontSize: "14px", fontFamily: "'DM Mono', monospace" }}>{s.value}</span>
                <span style={{ color: "#8b949e", fontSize: "13px" }}>{s.label}</span>
              </span>
            ))}
          </div>
        </div>

        {/* Tabs */}
        <div style={{ borderBottom: "1px solid rgba(255,255,255,0.1)", marginBottom: "24px", display: "flex", gap: "24px" }}>
          {["repos", "stars", "activity"].map(tab => (
            <button key={tab} className="tab-btn" onClick={() => setActiveTab(tab)} style={{
              color: activeTab === tab ? "#e6edf3" : "#8b949e",
              borderBottomColor: activeTab === tab ? "#f78166" : "transparent",
              fontWeight: activeTab === tab ? 600 : 400,
              textTransform: "capitalize",
            }}>
              {tab === "repos" && `📦 Repositories`}
              {tab === "stars" && `⭐ Stars`}
              {tab === "activity" && `📊 Activity`}
            </button>
          ))}
        </div>

        {activeTab === "repos" && (
          <div>
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(380px, 1fr))", gap: "16px" }}>
              {repos.map((r, i) => <RepoCard key={r.name} repo={r} index={i}/>)}
            </div>
          </div>
        )}

        {activeTab === "stars" && (
          <div style={{ animation: "fadeIn 0.4s ease both" }}>
            <div style={{ textAlign: "center", padding: "60px 20px", color: "#8b949e" }}>
              <div style={{ fontSize: "48px", marginBottom: "16px" }}>⭐</div>
              <p style={{ fontSize: "16px" }}>Starred repos would appear here</p>
              <p style={{ fontSize: "13px", marginTop: "8px" }}>Total stars earned: <strong style={{ color: "#f0c27f" }}>{totalStars.toLocaleString()}</strong></p>
            </div>
          </div>
        )}

        {activeTab === "activity" && (
          <div style={{ animation: "fadeIn 0.4s ease both" }}>
            {/* Contribution Graph */}
            <div style={{
              background: "rgba(255,255,255,0.03)", border: "1px solid rgba(255,255,255,0.07)",
              borderRadius: "12px", padding: "24px",
            }}>
              <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: "16px" }}>
                <span style={{ fontSize: "14px", color: "#8b949e" }}>1,247 contributions in the last year</span>
                <span style={{ fontSize: "13px", color: "#58a6ff", cursor: "pointer" }}>View all →</span>
              </div>
              <div style={{ display: "flex", flexDirection: "column", gap: "3px" }}>
                {contributions.map((row, ri) => (
                  <div key={ri} style={{ display: "flex", gap: "3px" }}>
                    {row.map((val, ci) => (
                      <div key={ci}
                        onMouseEnter={(e) => setTooltip({ val, x: e.clientX, y: e.clientY })}
                        onMouseLeave={() => setTooltip(null)}
                        style={{
                          width: "14px", height: "14px", borderRadius: "3px",
                          background: intensityColor(val),
                          cursor: "pointer",
                          transition: "transform 0.1s",
                          flexShrink: 0,
                        }}
                      />
                    ))}
                  </div>
                ))}
              </div>
              <div style={{ display: "flex", alignItems: "center", gap: "6px", marginTop: "12px", justifyContent: "flex-end" }}>
                <span style={{ color: "#8b949e", fontSize: "11px" }}>Less</span>
                {[0,1,2,3,4].map(v => (
                  <div key={v} style={{ width: "10px", height: "10px", borderRadius: "2px", background: intensityColor(v) }}/>
                ))}
                <span style={{ color: "#8b949e", fontSize: "11px" }}>More</span>
              </div>
            </div>

            {/* Stats Cards */}
            <div style={{ display: "grid", gridTemplateColumns: "repeat(3, 1fr)", gap: "16px", marginTop: "20px" }}>
              {[
                { icon: "💡", label: "Pull Requests", value: "482" },
                { icon: "🔀", label: "Issues Opened", value: "219" },
                { icon: "🧩", label: "Code Reviews", value: "1,034" },
              ].map(s => (
                <div key={s.label} style={{
                  background: "rgba(255,255,255,0.03)", border: "1px solid rgba(255,255,255,0.07)",
                  borderRadius: "12px", padding: "20px", textAlign: "center",
                }}>
                  <div style={{ fontSize: "28px", marginBottom: "8px" }}>{s.icon}</div>
                  <div style={{ fontSize: "22px", fontWeight: 700, fontFamily: "'DM Mono', monospace", color: "#e6edf3" }}>{s.value}</div>
                  <div style={{ fontSize: "12px", color: "#8b949e", marginTop: "4px" }}>{s.label}</div>
                </div>
              ))}
            </div>
          </div>
        )}
      </div>
    </div>
  );
}
