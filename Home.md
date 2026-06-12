---
cssclasses:
  - synthwave-home
---
<div class="sw-root">
<div class="sw-sky"></div>
<div class="sw-sun"></div>
<div class="sw-horizon"></div>
<div class="sw-vignette"></div>
<div class="sw-scanlines"></div>
<div class="sw-grain"></div>
<div class="sw-page">
<div class="sw-topbar mono">
<span class="sw-clock" id="sw-clock">--:--:--</span>
<span id="sw-date">Friday 12 June</span>
<span class="sw-right"><span class="sw-ok">● Sync OK</span><span>Odysseus</span></span>
</div>
<div class="sw-h1"><span class="sw-grad" id="sw-greet">Good evening, Jordon.</span><br><span class="sw-dim">Where to?</span></div>
<div class="sw-search" id="sw-search" role="button" tabindex="0" aria-label="Open quick switcher">
<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="11" cy="11" r="7"/><path d="m20 20-3.5-3.5"/></svg>
<span>Search the vault</span>
<kbd>⌘O</kbd>
</div>
<nav class="sw-grid">
<a class="sw-app c-magenta internal-link" data-href="Dev/Dev" href="Dev/Dev">
<span class="sw-glyph"><svg viewBox="0 0 24 24"><path d="m8 9-3 3 3 3"/><path d="m16 9 3 3-3 3"/><path d="m13 7-2 10"/></svg></span>
<span class="sw-label">Dev</span>
</a>
<a class="sw-app c-cyan internal-link" data-href="Learning/Learning" href="Learning/Learning">
<span class="sw-glyph"><svg viewBox="0 0 24 24"><path d="M4 7c2.5-1.5 5.5-1.5 8 0 2.5-1.5 5.5-1.5 8 0v11c-2.5-1.5-5.5-1.5-8 0-2.5-1.5-5.5-1.5-8 0Z"/><path d="M12 7v11"/></svg></span>
<span class="sw-label">Learning</span>
</a>
<a class="sw-app c-violet internal-link" data-href="Work/Work" href="Work/Work">
<span class="sw-glyph"><svg viewBox="0 0 24 24"><rect x="3" y="8" width="18" height="12" rx="2.5"/><path d="M9 8V6.5A2.5 2.5 0 0 1 11.5 4h1A2.5 2.5 0 0 1 15 6.5V8"/></svg></span>
<span class="sw-label">Work</span>
</a>
<a class="sw-app c-lime internal-link" data-href="Homelab/Homelab" href="Homelab/Homelab">
<span class="sw-glyph"><svg viewBox="0 0 24 24"><rect x="4" y="4" width="16" height="7" rx="2"/><rect x="4" y="13" width="16" height="7" rx="2"/><path d="M8 7.5h.01M8 16.5h.01"/></svg></span>
<span class="sw-label">Homelab</span>
</a>
<a class="sw-app c-amber internal-link" data-href="Tutoring/Tutoring" href="Tutoring/Tutoring">
<span class="sw-glyph"><svg viewBox="0 0 24 24"><path d="m12 4 9 4.5-9 4.5-9-4.5Z"/><path d="M6 10.8V15c0 1.5 2.7 3 6 3s6-1.5 6-3v-4.2"/></svg></span>
<span class="sw-label">Tutoring</span>
</a>
<a class="sw-app c-pink internal-link" data-href="Personal/Personal" href="Personal/Personal">
<span class="sw-glyph"><svg viewBox="0 0 24 24"><path d="M12 20s-7-4.3-7-9.5A4 4 0 0 1 12 8a4 4 0 0 1 7 2.5C19 15.7 12 20 12 20Z"/></svg></span>
<span class="sw-label">Personal</span>
</a>
</nav>
<div class="sw-actions">
<a class="sw-action internal-link" data-href="Daily" href="Daily">+ Daily note</a>
<a class="sw-action internal-link" data-href="Weekly review" href="Weekly review">↻ Weekly review</a>
<a class="sw-action internal-link" data-href="Vault map" href="Vault map">⌥ Vault map</a>
<a class="sw-action internal-link" data-href="Canvas" href="Canvas">◫ Canvas</a>
</div>
<div class="sw-stats">
<div class="sw-stat"><div class="sw-num" id="sw-notecount">—</div><div class="sw-k">Notes</div></div>
<div class="sw-stat"><div class="sw-num" id="sw-taskcount">—</div><div class="sw-k">Open tasks</div></div>
<div class="sw-stat"><div class="sw-num" id="sw-weekcount">—</div><div class="sw-k">New this week</div></div>
<div class="sw-stat"><div class="sw-num" id="sw-todaycount">—</div><div class="sw-k">Edited today</div></div>
</div>
<div class="sw-cards">
<section class="sw-card">
<div class="sw-h2">Recently edited</div>
<div id="sw-recent"></div>
</section>
<div>
<section class="sw-card">
<div class="sw-h2">Pinned</div>
<a class="sw-row internal-link" data-href="Weekly review" href="Weekly review"><span class="sw-title">Weekly review</span></a>
<a class="sw-row internal-link" data-href="Vault map" href="Vault map"><span class="sw-title">Vault map</span></a>
</section>
<section class="sw-card sw-pinned">
<div class="sw-h2">Transmission</div>
<div class="sw-transmission" style="margin-top:4px">
<span class="sw-k">// Incoming</span>
<p class="sw-q">"Simplicity is a great virtue but it requires hard work to achieve it." — Dijkstra</p>
</div>
</section>
</div>
</div>
<div class="sw-footer"><span id="sw-foot-left">Vault online</span><span>Odysseus // online</span></div>
</div>
</div>

```dataviewjs
// ---- live clock, greeting, real vault stats ----
const root = dv.container.closest(".markdown-preview-view") ?? document;
const $ = id => root.querySelector("#" + id);
const pad = x => String(x).padStart(2, "0");

function tick() {
  const n = new Date();
  if ($("sw-clock")) $("sw-clock").textContent = `${pad(n.getHours())}:${pad(n.getMinutes())}:${pad(n.getSeconds())}`;
  if ($("sw-date")) $("sw-date").textContent = n.toLocaleDateString("en-GB", { weekday: "short", day: "2-digit", month: "2-digit", year: "numeric" }).replaceAll("/", ".");
  const h = n.getHours();
  const g = h < 5 ? "Up late, Jordon." : h < 12 ? "Good morning, Jordon." : h < 18 ? "Good afternoon, Jordon." : "Good evening, Jordon.";
  if ($("sw-greet")) $("sw-greet").textContent = g;
}
tick();
const t = setInterval(tick, 1000);
this.register?.(() => clearInterval(t)); // tidy up on unload where supported

// make the search bar actually open the quick switcher
const searchEl = $("sw-search");
if (searchEl) {
  searchEl.addEventListener("click", () => app.commands.executeCommandById("switcher:open"));
  searchEl.addEventListener("keydown", e => { if (e.key === "Enter") app.commands.executeCommandById("switcher:open"); });
}

// stats
const pages = dv.pages().where(p => !p.file.path.startsWith("Templates"));
const now = window.moment();
if ($("sw-notecount")) $("sw-notecount").textContent = pages.length;
if ($("sw-taskcount")) $("sw-taskcount").textContent = pages.file.tasks.where(t => !t.completed).length;
if ($("sw-weekcount")) $("sw-weekcount").textContent = pages.where(p => now.diff(window.moment(p.file.ctime.toString()), "days") < 7).length;
if ($("sw-todaycount")) $("sw-todaycount").textContent = pages.where(p => window.moment(p.file.mtime.toString()).isSame(now, "day")).length;

// recently edited list
const dots = ["#8b5cf6", "#7dff7a", "#ffb84d", "#ff2d95"];
const recent = pages.sort(p => p.file.mtime, "desc").limit(4).values;
const box = $("sw-recent");
if (box) {
  box.innerHTML = "";
  recent.forEach((p, i) => {
    const a = document.createElement("a");
    a.className = "sw-row internal-link";
    a.dataset.href = p.file.path;
    a.href = p.file.path;
    const ago = window.moment(p.file.mtime.toString()).fromNow(true);
    a.innerHTML = `<span class="sw-dot" style="color:${dots[i]};background:${dots[i]}"></span><span class="sw-title">${p.file.name}</span><span class="sw-meta">${ago}</span>`;
    box.appendChild(a);
  });
}
if ($("sw-foot-left")) $("sw-foot-left").textContent = `${pages.length} notes · 6 spaces`;
```