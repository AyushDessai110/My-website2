<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FitQuest — Level Up Your Body</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f; --bg2: #111118; --bg3: #1a1a25; --card: #16161f;
    --border: rgba(255,255,255,0.07); --border2: rgba(255,255,255,0.13);
    --accent: #e8ff47; --accent2: #47ffb8; --accent3: #ff6b47;
    --text: #f0f0f5; --muted: #8888a0;
    --danger: #ff4757; --gold: #ffd700; --purple: #a855f7; --blue: #3b82f6;
    --font-display: 'Bebas Neue', sans-serif;
    --font-body: 'DM Sans', sans-serif;
    --font-mono: 'Space Mono', monospace;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body { background: var(--bg); color: var(--text); font-family: var(--font-body); min-height: 100vh; overflow-x: hidden; }

  /* ─── SCREENS ─── */
  .screen { display: none; min-height: 100vh; }
  .screen.active { display: flex; flex-direction: column; }

  /* ─── LOGIN ─── */
  #screen-login { background: var(--bg); align-items: center; justify-content: center; position: relative; overflow: hidden; }
  .login-bg { position: absolute; inset: 0; background: radial-gradient(ellipse 60% 50% at 80% 20%, rgba(232,255,71,0.08) 0%, transparent 60%), radial-gradient(ellipse 50% 40% at 20% 80%, rgba(71,255,184,0.06) 0%, transparent 60%); pointer-events: none; }
  .login-grid { position: absolute; inset: 0; background-image: linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px); background-size: 40px 40px; pointer-events: none; }
  .login-box { position: relative; z-index: 1; width: min(420px, 90vw); background: var(--card); border: 1px solid var(--border2); border-radius: 20px; padding: 2.5rem 2rem; }
  .login-logo { text-align: center; margin-bottom: 2rem; }
  .login-logo .logo-text { font-family: var(--font-display); font-size: 3.5rem; letter-spacing: 3px; background: linear-gradient(135deg, var(--accent), var(--accent2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; line-height: 1; }
  .login-logo p { color: var(--muted); font-size: 0.85rem; margin-top: 0.3rem; letter-spacing: 2px; text-transform: uppercase; }
  .tabs { display: flex; background: var(--bg3); border-radius: 10px; padding: 4px; margin-bottom: 1.5rem; gap: 4px; }
  .tab-btn { flex: 1; padding: 0.5rem; background: transparent; border: none; border-radius: 8px; color: var(--muted); font-family: var(--font-body); font-size: 0.85rem; font-weight: 500; cursor: pointer; transition: all 0.2s; }
  .tab-btn.active { background: var(--accent); color: #000; }
  .form-group { margin-bottom: 1rem; }
  .form-group label { display: block; font-size: 0.8rem; color: var(--muted); margin-bottom: 0.35rem; letter-spacing: 1px; text-transform: uppercase; }
  .form-group input, .form-group select { width: 100%; background: var(--bg3); border: 1px solid var(--border); border-radius: 10px; padding: 0.75rem 1rem; color: var(--text); font-family: var(--font-body); font-size: 0.9rem; outline: none; transition: border-color 0.2s; }
  .form-group input:focus, .form-group select:focus { border-color: var(--accent); }
  .form-group select option { background: var(--bg3); }
  .btn-primary { width: 100%; padding: 0.85rem; background: var(--accent); border: none; border-radius: 10px; color: #000; font-family: var(--font-body); font-size: 0.95rem; font-weight: 600; cursor: pointer; transition: all 0.2s; letter-spacing: 0.5px; margin-top: 0.5rem; }
  .btn-primary:hover { opacity: 0.9; transform: translateY(-1px); }
  .btn-primary:active { transform: translateY(0); }
  .login-form { display: none; }
  .login-form.active { display: block; }

  /* ─── TOP NAV ─── */
  .topnav { background: rgba(10,10,15,0.95); backdrop-filter: blur(12px); border-bottom: 1px solid var(--border); padding: 0 1.5rem; height: 56px; display: flex; align-items: center; justify-content: space-between; position: sticky; top: 0; z-index: 100; flex-shrink: 0; }
  .nav-logo { font-family: var(--font-display); font-size: 1.6rem; letter-spacing: 2px; background: linear-gradient(135deg, var(--accent), var(--accent2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .nav-user { display: flex; align-items: center; gap: 0.75rem; }
  .nav-avatar { width: 34px; height: 34px; background: linear-gradient(135deg, var(--accent), var(--accent2)); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700; font-size: 0.8rem; color: #000; cursor: pointer; }
  .nav-username { font-size: 0.85rem; color: var(--muted); }

  /* ─── BOTTOM NAV (5 items) ─── */
  .bottomnav { position: fixed; bottom: 0; left: 0; right: 0; background: rgba(10,10,15,0.97); backdrop-filter: blur(16px); border-top: 1px solid var(--border); display: flex; height: 64px; z-index: 100; }
  .nav-item { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 2px; cursor: pointer; transition: all 0.2s; border: none; background: transparent; color: var(--muted); font-family: var(--font-body); font-size: 0.58rem; letter-spacing: 0.3px; }
  .nav-item.active { color: var(--accent); }
  .nav-item svg { width: 20px; height: 20px; }

  /* ─── PAGE CONTENT ─── */
  .page-content { flex: 1; overflow-y: auto; padding: 1.25rem 1rem 80px; }

  /* ─── HOME ─── */
  .welcome-header { margin-bottom: 1.25rem; }
  .welcome-header .greeting { font-size: 0.8rem; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; }
  .welcome-header h1 { font-family: var(--font-display); font-size: 2.2rem; letter-spacing: 1px; line-height: 1.1; margin-top: 0.2rem; }
  .welcome-header h1 span { color: var(--accent); }
  .stats-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.6rem; margin-bottom: 1.25rem; }
  .stat-card { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 0.85rem 0.75rem; text-align: center; }
  .stat-card .stat-val { font-family: var(--font-display); font-size: 1.8rem; letter-spacing: 1px; line-height: 1; }
  .stat-card .stat-val.streak { color: var(--accent3); }
  .stat-card .stat-val.workouts { color: var(--accent2); }
  .stat-card .stat-val.points { color: var(--purple); }
  .stat-card .stat-label { font-size: 0.65rem; color: var(--muted); margin-top: 0.25rem; letter-spacing: 1px; text-transform: uppercase; }
  .level-bar-wrap { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 1rem; margin-bottom: 1.25rem; }
  .level-header { display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 0.6rem; }
  .level-header .level-name { font-weight: 600; font-size: 0.9rem; }
  .level-header .level-xp { font-family: var(--font-mono); font-size: 0.75rem; color: var(--muted); }
  .progress-bar { height: 8px; background: var(--bg3); border-radius: 99px; overflow: hidden; }
  .progress-fill { height: 100%; border-radius: 99px; background: linear-gradient(90deg, var(--purple), var(--accent)); transition: width 0.5s ease; }
  .start-workout-btn { display: flex; align-items: center; justify-content: center; gap: 0.75rem; width: 100%; padding: 1rem; background: var(--accent); border: none; border-radius: 14px; color: #000; font-family: var(--font-body); font-size: 1rem; font-weight: 700; cursor: pointer; transition: all 0.2s; margin-bottom: 1.25rem; letter-spacing: 0.5px; }
  .start-workout-btn:hover { opacity: 0.9; transform: translateY(-1px); }
  .challenge-card { background: linear-gradient(135deg, rgba(168,85,247,0.15), rgba(59,130,246,0.1)); border: 1px solid rgba(168,85,247,0.3); border-radius: 16px; padding: 1.1rem; margin-bottom: 1.25rem; }
  .challenge-card .ch-tag { font-size: 0.65rem; letter-spacing: 2px; text-transform: uppercase; color: var(--purple); margin-bottom: 0.4rem; font-weight: 600; }
  .challenge-card h3 { font-family: var(--font-display); font-size: 1.5rem; letter-spacing: 1px; color: var(--text); margin-bottom: 0.3rem; }
  .challenge-card .ch-reward { display: flex; align-items: center; gap: 0.4rem; font-size: 0.8rem; color: var(--gold); font-weight: 600; }
  .ch-complete-btn { width: 100%; padding: 0.65rem; background: transparent; border: 1px solid var(--purple); border-radius: 10px; color: var(--purple); font-family: var(--font-body); font-size: 0.85rem; font-weight: 600; cursor: pointer; margin-top: 0.75rem; transition: all 0.2s; }
  .ch-complete-btn:hover { background: rgba(168,85,247,0.1); }
  .step-tracker-card { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 1.1rem; margin-bottom: 1.25rem; }
  .step-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.75rem; }
  .step-count { font-family: var(--font-display); font-size: 2.5rem; letter-spacing: 2px; color: var(--accent2); line-height: 1; }
  .section-title { font-family: var(--font-display); font-size: 1.3rem; letter-spacing: 1px; margin-bottom: 0.75rem; color: var(--text); }

  /* ─── WORKOUT ─── */
  .workout-panel { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 1.25rem; margin-bottom: 1rem; }
  .timer-display { text-align: center; padding: 1.5rem 0; }
  .timer-display .time { font-family: var(--font-display); font-size: 5rem; letter-spacing: 4px; color: var(--accent); line-height: 1; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.6} }
  .timer-controls { display: flex; gap: 0.75rem; margin-bottom: 1rem; }
  .btn-green { flex: 1; padding: 0.75rem; background: rgba(71,255,184,0.15); border: 1px solid rgba(71,255,184,0.4); border-radius: 12px; color: var(--accent2); font-family: var(--font-body); font-weight: 600; font-size: 0.9rem; cursor: pointer; transition: all 0.2s; }
  .btn-green:hover { background: rgba(71,255,184,0.25); }
  .btn-red { flex: 1; padding: 0.75rem; background: rgba(255,71,87,0.12); border: 1px solid rgba(255,71,87,0.35); border-radius: 12px; color: var(--danger); font-family: var(--font-body); font-weight: 600; font-size: 0.9rem; cursor: pointer; transition: all 0.2s; }
  .btn-red:hover { background: rgba(255,71,87,0.22); }
  .exercise-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.6rem; margin-bottom: 1rem; }
  .ex-card { background: var(--bg3); border: 1px solid var(--border); border-radius: 12px; padding: 0.85rem; cursor: pointer; transition: all 0.2s; text-align: center; }
  .ex-card:hover { border-color: var(--border2); }
  .ex-card.selected { border-color: var(--accent); background: rgba(232,255,71,0.07); }
  .ex-card .ex-icon { font-size: 1.8rem; margin-bottom: 0.3rem; }
  .ex-card .ex-name { font-size: 0.8rem; font-weight: 600; }
  .ex-card .ex-muscle { font-size: 0.65rem; color: var(--muted); margin-top: 0.15rem; }
  .rep-counter-box { text-align: center; padding: 1.5rem 0; background: var(--card); border: 1px solid var(--border); border-radius: 16px; margin-bottom: 1rem; }
  .rep-count { font-family: var(--font-display); font-size: 7rem; letter-spacing: 4px; color: var(--accent); line-height: 1; }
  .rep-label { font-size: 0.8rem; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; margin-top: 0.25rem; }
  .rep-btn-row { display: flex; gap: 0.75rem; justify-content: center; margin-top: 1.25rem; padding: 0 1.25rem; }
  .rep-btn { flex: 1; padding: 0.9rem; font-family: var(--font-display); font-size: 1.8rem; letter-spacing: 1px; border: none; border-radius: 14px; cursor: pointer; transition: all 0.15s; }
  .rep-btn:active { transform: scale(0.95); }
  .rep-btn-add { background: var(--accent); color: #000; }
  .rep-btn-reset { background: var(--bg3); border: 1px solid var(--border2); color: var(--muted); font-size: 1rem; flex: 0.6; }
  .anticheat-warn { background: rgba(255,71,87,0.1); border: 1px solid rgba(255,71,87,0.3); border-radius: 10px; padding: 0.6rem 0.85rem; font-size: 0.75rem; color: var(--danger); margin-top: 0.5rem; display: none; }
  .anticheat-warn.show { display: block; }

  /* ─── PROGRESS ─── */
  .prog-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.75rem; margin-bottom: 1.25rem; }
  .prog-card { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 1rem; }
  .prog-card .prog-val { font-family: var(--font-display); font-size: 2rem; letter-spacing: 1px; line-height: 1; }
  .prog-card .prog-lbl { font-size: 0.7rem; color: var(--muted); margin-top: 0.2rem; letter-spacing: 1px; text-transform: uppercase; }
  .prog-card .prog-change { font-size: 0.72rem; margin-top: 0.3rem; font-weight: 600; }
  .prog-change.up { color: var(--accent2); }
  .week-chart { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 1rem; margin-bottom: 1.25rem; }
  .chart-bars { display: flex; align-items: flex-end; gap: 4px; height: 80px; margin-top: 0.75rem; }
  .chart-bar-wrap { flex: 1; display: flex; flex-direction: column; align-items: center; height: 100%; justify-content: flex-end; gap: 4px; }
  .chart-bar { width: 100%; border-radius: 4px 4px 0 0; background: linear-gradient(180deg, var(--accent2), rgba(71,255,184,0.3)); transition: height 0.4s ease; min-height: 3px; }
  .chart-bar.today { background: linear-gradient(180deg, var(--accent), rgba(232,255,71,0.3)); }
  .chart-label { font-size: 0.6rem; color: var(--muted); }
  .badges-wrap { display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.6rem; margin-bottom: 1.25rem; }
  .badge-item { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 0.85rem 0.6rem; text-align: center; }
  .badge-item.locked { opacity: 0.35; filter: grayscale(1); }
  .badge-item.unlocked { border-color: var(--gold); background: rgba(255,215,0,0.05); }
  .badge-icon { font-size: 2rem; }
  .badge-name { font-size: 0.65rem; font-weight: 600; margin-top: 0.25rem; }
  .badge-desc { font-size: 0.6rem; color: var(--muted); margin-top: 0.1rem; }

  /* ─── PROFILE ─── */
  .plan-card { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 1.25rem; margin-bottom: 1rem; }
  .plan-card h3 { font-family: var(--font-display); font-size: 1.3rem; letter-spacing: 1px; margin-bottom: 1rem; }
  .plan-opt { display: flex; align-items: center; gap: 0.75rem; padding: 0.65rem 0.85rem; background: var(--bg3); border: 1px solid var(--border); border-radius: 10px; margin-bottom: 0.5rem; cursor: pointer; transition: all 0.2s; }
  .plan-opt.selected { border-color: var(--accent); background: rgba(232,255,71,0.05); }
  .plan-opt .dot { width: 16px; height: 16px; border-radius: 50%; border: 2px solid var(--muted); flex-shrink: 0; transition: all 0.2s; }
  .plan-opt.selected .dot { background: var(--accent); border-color: var(--accent); }
  .plan-opt .opt-text { font-size: 0.85rem; }
  .generate-plan-btn { width: 100%; padding: 0.85rem; background: linear-gradient(135deg, var(--purple), var(--blue)); border: none; border-radius: 12px; color: #fff; font-family: var(--font-body); font-weight: 700; font-size: 0.95rem; cursor: pointer; margin-top: 0.5rem; }
  .generated-plan { background: var(--bg3); border: 1px solid var(--border2); border-radius: 12px; padding: 1rem; margin-top: 1rem; font-size: 0.85rem; line-height: 1.7; display: none; }
  .generated-plan.show { display: block; }
  .generated-plan h4 { color: var(--accent); font-family: var(--font-display); font-size: 1.1rem; margin-bottom: 0.5rem; }

  /* ─── MODAL ─── */
  .modal-overlay { position: fixed; inset: 0; background: rgba(0,0,0,0.85); backdrop-filter: blur(8px); z-index: 200; display: none; align-items: center; justify-content: center; padding: 1rem; }
  .modal-overlay.open { display: flex; }
  .modal-box { background: var(--card); border: 1px solid var(--border2); border-radius: 20px; padding: 1.75rem 1.5rem; width: min(380px, 100%); text-align: center; }
  .modal-box h2 { font-family: var(--font-display); font-size: 2rem; letter-spacing: 2px; color: var(--accent); margin-bottom: 0.5rem; }
  .summary-stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.6rem; margin: 1.25rem 0; }
  .sum-stat { background: var(--bg3); border-radius: 10px; padding: 0.75rem 0.5rem; }
  .sum-stat .sv { font-family: var(--font-display); font-size: 1.6rem; letter-spacing: 1px; }
  .sum-stat .sl { font-size: 0.6rem; color: var(--muted); margin-top: 0.1rem; }
  .xp-earned { background: rgba(168,85,247,0.12); border: 1px solid rgba(168,85,247,0.3); border-radius: 10px; padding: 0.75rem; margin-bottom: 1rem; font-size: 0.9rem; font-weight: 600; color: var(--purple); }
  .modal-close { width: 100%; padding: 0.8rem; background: var(--accent); border: none; border-radius: 10px; color: #000; font-weight: 700; font-size: 0.95rem; cursor: pointer; font-family: var(--font-body); }

  /* ─── TOAST ─── */
  .toast { position: fixed; top: 1rem; left: 50%; transform: translateX(-50%) translateY(-80px); background: var(--card); border: 1px solid var(--border2); border-radius: 12px; padding: 0.75rem 1.25rem; font-size: 0.85rem; font-weight: 500; z-index: 300; transition: transform 0.35s cubic-bezier(0.34,1.56,0.64,1); white-space: nowrap; max-width: 90vw; }
  .toast.show { transform: translateX(-50%) translateY(0); }

  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 2px; }
  @media (min-width: 500px) { .page-content { padding: 1.5rem 1.5rem 80px; } .login-box { padding: 3rem 2.5rem; } }

  /* ══════════════════════════════════════════════════════
     COMPETITION PAGE STYLES
     ══════════════════════════════════════════════════════ */

  /* Period selector */
  .period-tabs { display: flex; gap: 0.4rem; margin-bottom: 1rem; }
  .period-btn { flex: 1; padding: 0.45rem 0.4rem; background: var(--bg3); border: 1px solid var(--border); border-radius: 8px; color: var(--muted); font-family: var(--font-body); font-size: 0.72rem; font-weight: 600; cursor: pointer; transition: all 0.2s; }
  .period-btn.active { background: var(--accent); color: #000; border-color: var(--accent); }

  /* Type toggle */
  .type-toggle { display: flex; background: var(--bg3); border-radius: 12px; padding: 4px; gap: 4px; margin-bottom: 1rem; }
  .type-btn { flex: 1; padding: 0.6rem; background: transparent; border: none; border-radius: 9px; color: var(--muted); font-family: var(--font-body); font-size: 0.82rem; font-weight: 600; cursor: pointer; transition: all 0.2s; display: flex; align-items: center; justify-content: center; gap: 0.4rem; }
  .type-btn.active { background: var(--card); color: var(--text); box-shadow: 0 2px 8px rgba(0,0,0,0.4); }

  /* Leaderboard */
  .leaderboard-list { display: flex; flex-direction: column; gap: 0.5rem; margin-bottom: 1.25rem; }
  .lb-row { display: flex; align-items: center; gap: 0.75rem; padding: 0.75rem 0.9rem; background: var(--card); border: 1px solid var(--border); border-radius: 13px; transition: all 0.2s; position: relative; overflow: hidden; }
  .lb-row.me { border-color: var(--accent); background: rgba(232,255,71,0.05); }
  .lb-row.me::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 3px; background: var(--accent); }
  .lb-rank { font-family: var(--font-display); font-size: 1.4rem; width: 28px; text-align: center; flex-shrink: 0; }
  .lb-rank.r1 { color: var(--gold); }
  .lb-rank.r2 { color: #c0c0c0; }
  .lb-rank.r3 { color: #cd7f32; }
  .lb-rank.rme { color: var(--accent); }
  .lb-avatar { width: 34px; height: 34px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.7rem; font-weight: 700; color: #000; flex-shrink: 0; }
  .lb-info { flex: 1; min-width: 0; }
  .lb-name { font-size: 0.85rem; font-weight: 600; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .lb-name.me-name { color: var(--accent); }
  .lb-sub { font-size: 0.65rem; color: var(--muted); margin-top: 0.1rem; }
  .lb-stat { text-align: right; flex-shrink: 0; }
  .lb-val { font-family: var(--font-display); font-size: 1.2rem; letter-spacing: 1px; line-height: 1; }
  .lb-unit { font-size: 0.6rem; color: var(--muted); margin-top: 0.1rem; }
  .lb-bar-wrap { position: absolute; bottom: 0; left: 0; right: 0; height: 3px; background: var(--bg3); }
  .lb-bar { height: 100%; border-radius: 99px; transition: width 0.8s ease; }

  /* Duel button on leaderboard row */
  .duel-btn { padding: 0.3rem 0.65rem; background: transparent; border: 1px solid var(--accent3); border-radius: 7px; color: var(--accent3); font-family: var(--font-body); font-size: 0.7rem; font-weight: 600; cursor: pointer; flex-shrink: 0; transition: all 0.2s; }
  .duel-btn:hover { background: rgba(255,107,71,0.1); }

  /* Your rank banner */
  .rank-banner { background: linear-gradient(135deg, rgba(232,255,71,0.12), rgba(71,255,184,0.08)); border: 1px solid rgba(232,255,71,0.25); border-radius: 14px; padding: 1rem; margin-bottom: 1rem; display: flex; align-items: center; gap: 1rem; }
  .rank-badge { width: 54px; height: 54px; border-radius: 50%; background: linear-gradient(135deg, var(--accent), var(--accent2)); display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .rank-badge .rank-num { font-family: var(--font-display); font-size: 1.5rem; color: #000; letter-spacing: 1px; }
  .rank-details { flex: 1; }
  .rank-label { font-size: 0.65rem; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; }
  .rank-text { font-family: var(--font-display); font-size: 1.1rem; letter-spacing: 1px; margin-top: 0.15rem; }
  .rank-change { font-size: 0.72rem; margin-top: 0.2rem; }
  .rank-change.up { color: var(--accent2); }
  .rank-change.same { color: var(--muted); }

  /* Active Challenges */
  .active-challenge-card { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 1rem; margin-bottom: 0.85rem; position: relative; overflow: hidden; }
  .active-challenge-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg, var(--accent3), var(--purple)); }
  .ac-header { display: flex; align-items: center; gap: 0.65rem; margin-bottom: 0.75rem; }
  .ac-vs { font-size: 0.65rem; font-weight: 700; color: var(--accent3); letter-spacing: 2px; }
  .ac-opp-name { font-size: 0.88rem; font-weight: 600; flex: 1; }
  .ac-time { font-family: var(--font-mono); font-size: 0.7rem; color: var(--muted); }
  .ac-type-badge { font-size: 0.6rem; letter-spacing: 1px; text-transform: uppercase; padding: 0.2rem 0.5rem; border-radius: 6px; font-weight: 700; }
  .ac-type-badge.steps { background: rgba(71,255,184,0.15); color: var(--accent2); }
  .ac-type-badge.calories { background: rgba(255,107,71,0.15); color: var(--accent3); }

  .race-row { display: flex; align-items: center; gap: 0.65rem; margin-bottom: 0.5rem; }
  .race-avatar { width: 28px; height: 28px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.62rem; font-weight: 700; color: #000; flex-shrink: 0; }
  .race-name { font-size: 0.75rem; width: 52px; flex-shrink: 0; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .race-bar-wrap { flex: 1; height: 10px; background: var(--bg3); border-radius: 99px; overflow: hidden; position: relative; }
  .race-bar { height: 100%; border-radius: 99px; transition: width 0.6s ease; }
  .race-val { font-family: var(--font-mono); font-size: 0.7rem; width: 50px; text-align: right; flex-shrink: 0; }

  .ac-status { margin-top: 0.65rem; display: flex; align-items: center; justify-content: space-between; }
  .ac-status-text { font-size: 0.76rem; font-weight: 600; }
  .ac-status-text.winning { color: var(--accent2); }
  .ac-status-text.losing { color: var(--danger); }
  .ac-status-text.tied { color: var(--gold); }
  .ac-target { font-size: 0.68rem; color: var(--muted); }
  .ac-abandon-btn { padding: 0.25rem 0.6rem; background: transparent; border: 1px solid rgba(255,71,87,0.3); border-radius: 6px; color: var(--danger); font-size: 0.65rem; cursor: pointer; }

  /* Create Challenge button */
  .create-challenge-btn { width: 100%; padding: 0.85rem; background: transparent; border: 1px dashed var(--border2); border-radius: 14px; color: var(--muted); font-family: var(--font-body); font-size: 0.88rem; font-weight: 600; cursor: pointer; transition: all 0.2s; display: flex; align-items: center; justify-content: center; gap: 0.5rem; margin-bottom: 1.25rem; }
  .create-challenge-btn:hover { border-color: var(--accent); color: var(--accent); background: rgba(232,255,71,0.04); }

  /* Challenge History */
  .hist-row { display: flex; align-items: center; gap: 0.65rem; padding: 0.65rem 0.85rem; background: var(--card); border: 1px solid var(--border); border-radius: 12px; margin-bottom: 0.4rem; }
  .hist-icon { font-size: 1.1rem; flex-shrink: 0; }
  .hist-info { flex: 1; }
  .hist-title { font-size: 0.82rem; font-weight: 600; }
  .hist-sub { font-size: 0.66rem; color: var(--muted); margin-top: 0.1rem; }
  .hist-xp { font-family: var(--font-mono); font-size: 0.72rem; color: var(--purple); font-weight: 600; }

  /* Home competition snippet */
  .comp-snippet { background: linear-gradient(135deg, rgba(255,107,71,0.12), rgba(168,85,247,0.08)); border: 1px solid rgba(255,107,71,0.25); border-radius: 14px; padding: 0.9rem 1rem; margin-bottom: 1.25rem; cursor: pointer; }
  .comp-snippet-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 0.6rem; }
  .comp-snippet-title { font-size: 0.65rem; letter-spacing: 2px; text-transform: uppercase; color: var(--accent3); font-weight: 700; }
  .comp-snippet-rank { font-family: var(--font-display); font-size: 1rem; letter-spacing: 1px; }

  /* Create Challenge Modal */
  .ch-modal-section { margin-bottom: 1rem; text-align: left; }
  .ch-modal-label { font-size: 0.72rem; color: var(--muted); letter-spacing: 1px; text-transform: uppercase; margin-bottom: 0.45rem; display: block; }
  .type-select-row { display: flex; gap: 0.5rem; }
  .type-select-btn { flex: 1; padding: 0.65rem; background: var(--bg3); border: 1px solid var(--border); border-radius: 10px; color: var(--muted); font-family: var(--font-body); font-size: 0.82rem; font-weight: 600; cursor: pointer; transition: all 0.2s; display: flex; align-items: center; justify-content: center; gap: 0.4rem; }
  .type-select-btn.active { border-color: var(--accent); color: var(--accent); background: rgba(232,255,71,0.07); }
  .dur-select-row { display: flex; gap: 0.4rem; }
  .dur-btn { flex: 1; padding: 0.5rem; background: var(--bg3); border: 1px solid var(--border); border-radius: 8px; color: var(--muted); font-family: var(--font-body); font-size: 0.76rem; font-weight: 600; cursor: pointer; transition: all 0.2s; }
  .dur-btn.active { border-color: var(--accent); color: var(--accent); background: rgba(232,255,71,0.06); }
  .opp-select-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.45rem; max-height: 200px; overflow-y: auto; }
  .opp-btn { display: flex; align-items: center; gap: 0.5rem; padding: 0.55rem 0.7rem; background: var(--bg3); border: 1px solid var(--border); border-radius: 10px; cursor: pointer; transition: all 0.2s; }
  .opp-btn.active { border-color: var(--accent3); background: rgba(255,107,71,0.07); }
  .opp-av { width: 28px; height: 28px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.62rem; font-weight: 700; color: #000; flex-shrink: 0; }
  .opp-name-sm { font-size: 0.76rem; font-weight: 600; }
  .opp-stat-sm { font-size: 0.62rem; color: var(--muted); }
  .target-input { width: 100%; background: var(--bg3); border: 1px solid var(--border); border-radius: 10px; padding: 0.65rem 1rem; color: var(--text); font-family: var(--font-mono); font-size: 1rem; font-weight: 700; outline: none; transition: border-color 0.2s; text-align: center; }
  .target-input:focus { border-color: var(--accent); }
  .modal-start-btn { width: 100%; padding: 0.85rem; background: var(--accent3); border: none; border-radius: 12px; color: #fff; font-family: var(--font-body); font-size: 0.95rem; font-weight: 700; cursor: pointer; transition: all 0.2s; margin-top: 0.5rem; display: flex; align-items: center; justify-content: center; gap: 0.5rem; }
  .modal-start-btn:hover { opacity: 0.9; transform: translateY(-1px); }

  /* Result modal */
  .result-icon { font-size: 3.5rem; margin-bottom: 0.75rem; animation: bounceIn 0.5s ease; }
  @keyframes bounceIn { 0%{transform:scale(0.5);opacity:0} 70%{transform:scale(1.1)} 100%{transform:scale(1);opacity:1} }
  .result-vs { display: flex; align-items: center; gap: 0.75rem; justify-content: center; margin: 1rem 0; }
  .rv-card { flex: 1; background: var(--bg3); border-radius: 12px; padding: 0.75rem 0.5rem; text-align: center; }
  .rv-name { font-size: 0.75rem; color: var(--muted); margin-bottom: 0.25rem; }
  .rv-val { font-family: var(--font-display); font-size: 1.6rem; letter-spacing: 1px; }
  .rv-vs { font-family: var(--font-display); font-size: 1.4rem; color: var(--muted); }
</style>
</head>
<body>

<!-- ══════ LOGIN ══════ -->
<div id="screen-login" class="screen active">
  <div class="login-bg"></div>
  <div class="login-grid"></div>
  <div class="login-box">
    <div class="login-logo"><div class="logo-text">FITQUEST</div><p>Level up your body</p></div>
    <div class="tabs">
      <button class="tab-btn active" onclick="switchTab('login')">Login</button>
      <button class="tab-btn" onclick="switchTab('signup')">Sign Up</button>
    </div>
    <div id="form-login" class="login-form active">
      <div class="form-group"><label>Email</label><input type="email" id="login-email" placeholder="you@example.com"></div>
      <div class="form-group"><label>Password</label><input type="password" id="login-pass" placeholder="••••••••"></div>
      <button class="btn-primary" onclick="doLogin()">Log In</button>
    </div>
    <div id="form-signup" class="login-form">
      <div class="form-group"><label>Name</label><input type="text" id="signup-name" placeholder="Your name"></div>
      <div class="form-group"><label>Email</label><input type="email" id="signup-email" placeholder="you@example.com"></div>
      <div class="form-group"><label>Password</label><input type="password" id="signup-pass" placeholder="At least 6 characters"></div>
      <div class="form-group"><label>Fitness Goal</label>
        <select id="signup-goal"><option value="">Select your goal...</option><option value="weight_loss">Weight Loss</option><option value="muscle">Build Muscle</option><option value="endurance">Endurance</option><option value="flexibility">Flexibility</option><option value="general">General Fitness</option></select>
      </div>
      <div class="form-group"><label>Fitness Level</label>
        <select id="signup-level"><option value="">Select level...</option><option value="beginner">Beginner</option><option value="intermediate">Intermediate</option><option value="advanced">Advanced</option></select>
      </div>
      <button class="btn-primary" onclick="doSignup()">Create Account</button>
    </div>
  </div>
</div>

<!-- ══════ MAIN APP ══════ -->
<div id="screen-app" class="screen">

  <nav class="topnav">
    <div class="nav-logo">FITQUEST</div>
    <div class="nav-user">
      <span class="nav-username" id="nav-username"></span>
      <div class="nav-avatar" id="nav-avatar" onclick="doLogout()">–</div>
    </div>
  </nav>

  <!-- HOME PAGE -->
  <div id="page-home" class="page-content" style="display:block;">
    <div class="welcome-header">
      <div class="greeting">GOOD DAY,</div>
      <h1 id="home-name">CHAMPION <span>💪</span></h1>
    </div>
    <div class="stats-row">
      <div class="stat-card"><div class="stat-val streak" id="stat-streak">0🔥</div><div class="stat-label">Streak</div></div>
      <div class="stat-card"><div class="stat-val workouts" id="stat-workouts">0</div><div class="stat-label">Workouts</div></div>
      <div class="stat-card"><div class="stat-val points" id="stat-points">0</div><div class="stat-label">XP Points</div></div>
    </div>
    <div class="level-bar-wrap">
      <div class="level-header"><span class="level-name" id="level-name">Level 1 — Rookie</span><span class="level-xp" id="level-xp">0 / 100 XP</span></div>
      <div class="progress-bar"><div class="progress-fill" id="level-fill" style="width:0%"></div></div>
    </div>
    <!-- Competition Snippet -->
    <div class="comp-snippet" onclick="showPage('compete')">
      <div class="comp-snippet-header">
        <span class="comp-snippet-title">⚔️ Competition</span>
        <span class="comp-snippet-rank" id="home-rank-badge">—</span>
      </div>
      <div id="home-comp-preview" style="font-size:0.78rem;color:var(--muted);">Tap to see your ranking and challenge others</div>
    </div>
    <!-- Step Counter -->
    <div class="step-tracker-card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:0.5rem;">
        <span style="font-size:0.75rem;letter-spacing:2px;text-transform:uppercase;color:var(--muted);">STEPS TODAY</span>
        <span id="step-status" style="font-size:0.7rem;color:var(--accent2);">Detecting...</span>
      </div>
      <div class="step-row">
        <div class="step-count" id="step-count">0</div>
        <div style="text-align:right;"><div style="font-size:0.7rem;color:var(--muted);">Goal</div><div style="font-family:var(--font-display);font-size:1.2rem;color:var(--muted);">10,000</div></div>
      </div>
      <div class="progress-bar"><div class="progress-fill" id="step-fill" style="width:0%;background:linear-gradient(90deg,var(--accent2),var(--accent))"></div></div>
      <div style="margin-top:0.5rem;font-size:0.72rem;color:var(--muted);" id="step-msg">Walk around to count steps</div>
    </div>
    <!-- Daily Challenge -->
    <div class="challenge-card">
      <div class="ch-tag">⚡ DAILY CHALLENGE</div>
      <h3 id="ch-title">Loading...</h3>
      <div style="font-size:0.8rem;color:var(--muted);margin-bottom:0.4rem;" id="ch-desc"></div>
      <div class="ch-reward"><span>★</span><span id="ch-reward">+50 XP</span></div>
      <button class="ch-complete-btn" id="ch-btn" onclick="completeChallenge()">Mark Complete</button>
    </div>
    <button class="start-workout-btn" onclick="goToWorkout()">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polygon points="5 3 19 12 5 21 5 3"/></svg>
      START WORKOUT
    </button>
    <div class="section-title">ACHIEVEMENTS</div>
    <div class="badges-wrap" id="badges-home"></div>
  </div>

  <!-- WORKOUT PAGE -->
  <div id="page-workout" class="page-content" style="display:none;">
    <div class="section-title">WORKOUT SESSION</div>
    <div class="workout-panel">
      <div style="font-size:0.7rem;letter-spacing:2px;text-transform:uppercase;color:var(--muted);text-align:center;margin-bottom:0.5rem;">SESSION TIMER</div>
      <div class="timer-display"><div class="time" id="workout-timer">00:00</div><div style="font-size:0.7rem;color:var(--muted);margin-top:0.25rem;" id="timer-status">Ready to start</div></div>
      <div class="timer-controls"><button class="btn-green" id="timer-start-btn" onclick="startTimer()">▶ Start</button><button class="btn-red" onclick="endWorkout()">■ End Workout</button></div>
    </div>
    <div class="section-title">SELECT EXERCISE</div>
    <div class="exercise-grid" id="exercise-grid"></div>
    <div class="section-title">REP COUNTER</div>
    <div class="rep-counter-box">
      <div class="rep-count" id="rep-count-w">0</div>
      <div class="rep-label" id="current-exercise-name">SELECT AN EXERCISE</div>
      <div class="rep-btn-row"><button class="rep-btn rep-btn-reset" onclick="resetReps()">Reset</button><button class="rep-btn rep-btn-add" onclick="addRep()">+1</button></div>
    </div>
    <div class="anticheat-warn" id="anticheat-warn">⚠️ Too fast! Please count reps naturally.</div>
  </div>

  <!-- ══════════════════════════════════════════════════
       COMPETE PAGE
       ══════════════════════════════════════════════════ -->
  <div id="page-compete" class="page-content" style="display:none;">
    <div class="section-title">⚔️ COMPETE</div>

    <!-- Type toggle -->
    <div class="type-toggle">
      <button class="type-btn active" id="ctype-steps" onclick="setCompeteType('steps')">👟 Steps</button>
      <button class="type-btn" id="ctype-calories" onclick="setCompeteType('calories')">🔥 Calories</button>
    </div>

    <!-- Period -->
    <div class="period-tabs">
      <button class="period-btn active" id="period-today" onclick="setCompetePeriod('today')">Today</button>
      <button class="period-btn" id="period-week" onclick="setCompetePeriod('week')">This Week</button>
      <button class="period-btn" id="period-alltime" onclick="setCompetePeriod('alltime')">All Time</button>
    </div>

    <!-- Rank Banner -->
    <div class="rank-banner" id="rank-banner">
      <div class="rank-badge"><div class="rank-num" id="rank-num">—</div></div>
      <div class="rank-details">
        <div class="rank-label">YOUR RANK</div>
        <div class="rank-text" id="rank-text">Calculating...</div>
        <div class="rank-change same" id="rank-change">—</div>
      </div>
    </div>

    <!-- Leaderboard -->
    <div class="section-title" style="font-size:1rem;margin-bottom:0.6rem;">LEADERBOARD</div>
    <div class="leaderboard-list" id="leaderboard-list">
      <div style="text-align:center;padding:1.5rem;color:var(--muted);font-size:0.82rem;">Loading...</div>
    </div>

    <!-- Active Challenges -->
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:0.75rem;">
      <div class="section-title" style="font-size:1rem;margin:0;">ACTIVE CHALLENGES</div>
      <span id="active-ch-count" style="font-size:0.7rem;color:var(--muted);font-family:var(--font-mono);">0 / 3</span>
    </div>
    <div id="active-challenges-list"></div>

    <button class="create-challenge-btn" onclick="openCreateChallenge()">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="16"/><line x1="8" y1="12" x2="16" y2="12"/></svg>
      Create New Challenge
    </button>

    <!-- History -->
    <div class="section-title" style="font-size:1rem;margin-bottom:0.6rem;">PAST RESULTS</div>
    <div id="challenge-history">
      <div style="text-align:center;padding:1.25rem;color:var(--muted);font-size:0.8rem;">No challenges yet — start competing!</div>
    </div>
  </div>

  <!-- PROGRESS PAGE -->
  <div id="page-progress" class="page-content" style="display:none;">
    <div class="section-title">YOUR PROGRESS</div>
    <div class="prog-grid">
      <div class="prog-card"><div class="prog-val" id="prog-total" style="color:var(--accent2)">0</div><div class="prog-lbl">Total Workouts</div><div class="prog-change up" id="prog-streak-disp">🔥 0 day streak</div></div>
      <div class="prog-card"><div class="prog-val" id="prog-best-streak" style="color:var(--accent3)">0</div><div class="prog-lbl">Best Streak</div><div class="prog-change up">Days</div></div>
      <div class="prog-card"><div class="prog-val" id="prog-total-reps" style="color:var(--purple)">0</div><div class="prog-lbl">Total Reps</div><div class="prog-change up">All time</div></div>
      <div class="prog-card"><div class="prog-val" id="prog-calories" style="color:var(--gold)">0</div><div class="prog-lbl">Calories Burned</div><div class="prog-change up">Est. kcal</div></div>
    </div>
    <div class="week-chart">
      <div style="display:flex;justify-content:space-between;align-items:baseline;"><span class="section-title" style="margin:0;font-size:1rem;">WEEKLY WORKOUTS</span><span style="font-size:0.7rem;color:var(--muted);">This week</span></div>
      <div class="chart-bars" id="week-chart"></div>
    </div>
    <div class="section-title">EXERCISE BREAKDOWN</div>
    <div id="exercise-breakdown" style="margin-bottom:1.25rem;"></div>
    <div class="section-title">BADGES</div>
    <div class="badges-wrap" id="badges-full"></div>
  </div>

  <!-- PROFILE PAGE -->
  <div id="page-profile" class="page-content" style="display:none;">
    <div class="section-title">PERSONALIZE</div>
    <div class="plan-card">
      <h3>🎯 YOUR GOAL</h3>
      <div id="goal-opts">
        <div class="plan-opt selected" onclick="selectOpt('goal','weight_loss',this)"><div class="dot"></div><div class="opt-text">🔥 Weight Loss</div></div>
        <div class="plan-opt" onclick="selectOpt('goal','muscle',this)"><div class="dot"></div><div class="opt-text">💪 Build Muscle</div></div>
        <div class="plan-opt" onclick="selectOpt('goal','endurance',this)"><div class="dot"></div><div class="opt-text">🏃 Endurance</div></div>
        <div class="plan-opt" onclick="selectOpt('goal','flexibility',this)"><div class="dot"></div><div class="opt-text">🧘 Flexibility</div></div>
        <div class="plan-opt" onclick="selectOpt('goal','general',this)"><div class="dot"></div><div class="opt-text">⚡ General Fitness</div></div>
      </div>
    </div>
    <div class="plan-card">
      <h3>📊 FITNESS LEVEL</h3>
      <div id="level-opts">
        <div class="plan-opt selected" onclick="selectOpt('flevel','beginner',this)"><div class="dot"></div><div class="opt-text">🌱 Beginner</div></div>
        <div class="plan-opt" onclick="selectOpt('flevel','intermediate',this)"><div class="dot"></div><div class="opt-text">🌿 Intermediate</div></div>
        <div class="plan-opt" onclick="selectOpt('flevel','advanced',this)"><div class="dot"></div><div class="opt-text">🌳 Advanced</div></div>
      </div>
    </div>
    <button class="generate-plan-btn" onclick="generatePlan()">✨ Generate My Custom Plan</button>
    <div class="generated-plan" id="generated-plan"></div>
    <div class="plan-card" style="margin-top:1rem;">
      <h3>🔔 REMINDERS</h3>
      <div style="display:flex;justify-content:space-between;align-items:center;padding:0.6rem 0;border-bottom:1px solid var(--border);">
        <span style="font-size:0.85rem;">Workout Reminder</span>
        <label style="position:relative;width:44px;height:24px;display:block;"><input type="checkbox" id="rem-workout" onchange="toggleReminder('workout')" style="opacity:0;width:0;height:0;"><span id="rem-workout-track" style="position:absolute;inset:0;background:var(--bg3);border:1px solid var(--border2);border-radius:99px;cursor:pointer;transition:all 0.2s;"></span><span id="rem-workout-thumb" style="position:absolute;top:3px;left:3px;width:16px;height:16px;background:var(--muted);border-radius:50%;transition:all 0.2s;"></span></label>
      </div>
      <div style="display:flex;justify-content:space-between;align-items:center;padding:0.6rem 0;">
        <span style="font-size:0.85rem;">Streak Warning</span>
        <label style="position:relative;width:44px;height:24px;display:block;"><input type="checkbox" id="rem-streak" onchange="toggleReminder('streak')" style="opacity:0;width:0;height:0;"><span id="rem-streak-track" style="position:absolute;inset:0;background:var(--bg3);border:1px solid var(--border2);border-radius:99px;cursor:pointer;transition:all 0.2s;"></span><span id="rem-streak-thumb" style="position:absolute;top:3px;left:3px;width:16px;height:16px;background:var(--muted);border-radius:50%;transition:all 0.2s;"></span></label>
      </div>
    </div>
    <button class="btn-red" style="width:100%;border-radius:12px;padding:0.85rem;font-size:0.9rem;font-weight:600;" onclick="doLogout()">Sign Out</button>
  </div>

  <!-- BOTTOM NAV -->
  <nav class="bottomnav">
    <button class="nav-item active" id="nav-home" onclick="showPage('home')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>Home
    </button>
    <button class="nav-item" id="nav-workout" onclick="showPage('workout')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 4v16M18 4v16M2 12h4M18 12h4"/></svg>Workout
    </button>
    <button class="nav-item" id="nav-compete" onclick="showPage('compete')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>Compete
    </button>
    <button class="nav-item" id="nav-progress" onclick="showPage('progress')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>Progress
    </button>
    <button class="nav-item" id="nav-profile" onclick="showPage('profile')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>Profile
    </button>
  </nav>
</div>

<!-- Workout Summary Modal -->
<div class="modal-overlay" id="summary-modal">
  <div class="modal-box">
    <div style="font-size:2.5rem;margin-bottom:0.5rem;">🏆</div>
    <h2>WORKOUT DONE!</h2>
    <p style="font-size:0.8rem;color:var(--muted);margin-bottom:0.5rem;">Great session, champion!</p>
    <div class="summary-stats">
      <div class="sum-stat"><div class="sv" id="sum-time" style="color:var(--accent)">0:00</div><div class="sl">Duration</div></div>
      <div class="sum-stat"><div class="sv" id="sum-reps" style="color:var(--accent2)">0</div><div class="sl">Total Reps</div></div>
      <div class="sum-stat"><div class="sv" id="sum-cal" style="color:var(--gold)">0</div><div class="sl">Calories</div></div>
    </div>
    <div class="xp-earned" id="sum-xp">+0 XP Earned!</div>
    <button class="modal-close" onclick="closeSummary()">Continue</button>
  </div>
</div>

<!-- Create Challenge Modal -->
<div class="modal-overlay" id="create-challenge-modal">
  <div class="modal-box" style="max-height:90vh;overflow-y:auto;text-align:left;">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:1.25rem;">
      <h2 style="font-size:1.6rem;margin:0;">NEW CHALLENGE</h2>
      <button onclick="closeModal('create-challenge-modal')" style="background:none;border:none;color:var(--muted);font-size:1.3rem;cursor:pointer;">✕</button>
    </div>
    <div class="ch-modal-section">
      <span class="ch-modal-label">Compete in</span>
      <div class="type-select-row">
        <button class="type-select-btn active" id="cs-steps" onclick="setChallengeType('steps')">👟 Steps</button>
        <button class="type-select-btn" id="cs-calories" onclick="setChallengeType('calories')">🔥 Calories</button>
      </div>
    </div>
    <div class="ch-modal-section">
      <span class="ch-modal-label">Target <span id="cs-unit-label">steps</span></span>
      <input type="number" class="target-input" id="cs-target" placeholder="10000" min="100" max="100000">
      <div style="display:flex;gap:0.4rem;margin-top:0.5rem;" id="quick-targets">
        <button onclick="setQuickTarget(5000)"  style="flex:1;padding:0.3rem;background:var(--bg3);border:1px solid var(--border);border-radius:7px;color:var(--muted);font-size:0.7rem;cursor:pointer;">5K</button>
        <button onclick="setQuickTarget(10000)" style="flex:1;padding:0.3rem;background:var(--bg3);border:1px solid var(--border);border-radius:7px;color:var(--muted);font-size:0.7rem;cursor:pointer;">10K</button>
        <button onclick="setQuickTarget(15000)" style="flex:1;padding:0.3rem;background:var(--bg3);border:1px solid var(--border);border-radius:7px;color:var(--muted);font-size:0.7rem;cursor:pointer;">15K</button>
        <button onclick="setQuickTarget(20000)" style="flex:1;padding:0.3rem;background:var(--bg3);border:1px solid var(--border);border-radius:7px;color:var(--muted);font-size:0.7rem;cursor:pointer;">20K</button>
      </div>
    </div>
    <div class="ch-modal-section">
      <span class="ch-modal-label">Duration</span>
      <div class="dur-select-row">
        <button class="dur-btn active" id="dur-24" onclick="setDuration(24)">24h</button>
        <button class="dur-btn" id="dur-48" onclick="setDuration(48)">48h</button>
        <button class="dur-btn" id="dur-168" onclick="setDuration(168)">7 Days</button>
      </div>
    </div>
    <div class="ch-modal-section">
      <span class="ch-modal-label">Choose Opponent</span>
      <div class="opp-select-grid" id="opp-select-grid"></div>
    </div>
    <button class="modal-start-btn" onclick="startChallenge()">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
      Start Challenge!
    </button>
  </div>
</div>

<!-- Challenge Result Modal -->
<div class="modal-overlay" id="result-modal">
  <div class="modal-box">
    <div class="result-icon" id="result-icon">🏅</div>
    <h2 id="result-title">CHALLENGE OVER!</h2>
    <p id="result-subtitle" style="font-size:0.82rem;color:var(--muted);margin-bottom:0.75rem;"></p>
    <div class="result-vs">
      <div class="rv-card">
        <div class="rv-name">You</div>
        <div class="rv-val" id="rv-you" style="color:var(--accent)">0</div>
      </div>
      <div class="rv-vs">VS</div>
      <div class="rv-card">
        <div class="rv-name" id="rv-opp-name">Opponent</div>
        <div class="rv-val" id="rv-opp" style="color:var(--accent3)">0</div>
      </div>
    </div>
    <div class="xp-earned" id="result-xp">+0 XP</div>
    <button class="modal-close" onclick="closeModal('result-modal')">Continue</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
'use strict';

// ══════════════════════════════════════════
// CONSTANTS
// ══════════════════════════════════════════
const LEVELS = [
  {name:'Rookie',xp:0},{name:'Beginner',xp:100},{name:'Fighter',xp:250},
  {name:'Warrior',xp:500},{name:'Elite',xp:900},{name:'Champion',xp:1400},
  {name:'Legend',xp:2000},{name:'Master',xp:3000},{name:'Grandmaster',xp:4500},{name:'God Mode',xp:7000}
];

const EXERCISES = [
  {id:'pushup',name:'Push-ups',muscle:'Chest / Arms',icon:'💪',cal:0.5},
  {id:'squat',name:'Squats',muscle:'Legs / Glutes',icon:'🦵',cal:0.4},
  {id:'situp',name:'Sit-ups',muscle:'Core',icon:'🏋',cal:0.3},
  {id:'pullup',name:'Pull-ups',muscle:'Back / Biceps',icon:'🤸',cal:0.6},
  {id:'lunge',name:'Lunges',muscle:'Legs',icon:'🦿',cal:0.35},
  {id:'burpee',name:'Burpees',muscle:'Full Body',icon:'⚡',cal:0.9},
  {id:'plank',name:'Plank',muscle:'Core',icon:'🧘',cal:0.2},
  {id:'jumpingjack',name:'Jumping Jacks',muscle:'Cardio',icon:'🏃',cal:0.4}
];

const BADGES = [
  {id:'first',icon:'🎯',name:'First Blood',desc:'Complete 1st workout',req:u=>u.workouts>=1},
  {id:'w5',icon:'🔥',name:'On Fire',desc:'5 workouts done',req:u=>u.workouts>=5},
  {id:'w10',icon:'💥',name:'Dedicated',desc:'10 workouts done',req:u=>u.workouts>=10},
  {id:'s3',icon:'⚡',name:'3-Day Streak',desc:'3 days in a row',req:u=>u.bestStreak>=3},
  {id:'s7',icon:'🌟',name:'Streak Master',desc:'7-day streak',req:u=>u.bestStreak>=7},
  {id:'r100',icon:'💯',name:'Centurion',desc:'100 total reps',req:u=>u.totalReps>=100},
  {id:'r500',icon:'🏆',name:'Rep Monster',desc:'500 total reps',req:u=>u.totalReps>=500},
  {id:'steps',icon:'👟',name:'Step Starter',desc:'Reached 5,000 steps',req:u=>(u.steps||0)>=5000},
  {id:'ch5',icon:'🎖',name:'Challenger',desc:'5 daily challenges',req:u=>u.challenges>=5},
  // Competition Badges
  {id:'cw1',icon:'🥇',name:'First Win',desc:'Win your 1st challenge',req:u=>(u.compWins||0)>=1},
  {id:'cw5',icon:'🏅',name:'Hat Trick+',desc:'Win 5 challenges',req:u=>(u.compWins||0)>=5},
  {id:'cw10',icon:'👑',name:'Unbeatable',desc:'Win 10 challenges',req:u=>(u.compWins||0)>=10},
  {id:'stepking',icon:'🦶',name:'Step King',desc:'Rank #1 in daily steps',req:u=>(u.stepRankOnes||0)>=1},
  {id:'calking',icon:'🔥',name:'Calorie King',desc:'Rank #1 in daily calories',req:u=>(u.calRankOnes||0)>=1},
  {id:'streak3w',icon:'⚡',name:'Win Streak',desc:'Win 3 challenges in a row',req:u=>(u.winStreak||0)>=3},
];

const CHALLENGES_DAILY = [
  {title:'50 Push-ups',desc:'Complete 50 push-ups throughout the day',reward:60},
  {title:'100 Squats',desc:'100 squats — break into sets if needed',reward:70},
  {title:'5-Min Plank',desc:'Hold a plank for a total of 5 minutes',reward:80},
  {title:'200 Jumping Jacks',desc:'Get that heart pumping!',reward:50},
  {title:'50 Pull-ups',desc:'Challenge your back and biceps',reward:90},
  {title:'30-Min Walk',desc:'Walk for at least 30 continuous minutes',reward:55},
  {title:'Burpee Blitz: 30 Reps',desc:'Full body burn — no stopping!',reward:100},
  {title:'Core Circuit',desc:'50 sit-ups + 50 leg raises + 2-min plank',reward:85}
];

const PLANS = {
  weight_loss:{
    beginner:['Mon: 30min walk + 20 squats + 10 pushups','Tue: Rest / Stretch','Wed: 20 jumping jacks × 5 + 15 sit-ups','Thu: 30min brisk walk','Fri: 3×15 squats + 3×10 pushups','Sat: Yoga / Light stretch','Sun: Rest'],
    intermediate:['Mon: 4×20 squats + 4×15 pushups + 20 burpees','Tue: 40min run','Wed: HIIT 8 rounds','Thu: 30min swim','Fri: Full body circuit 45min','Sat: 5km jog','Sun: Rest'],
    advanced:['Mon: 5×25 burpees + 5×20 pullups','Tue: 60min run + core','Wed: Heavy compound lifts','Thu: HIIT + sprints','Fri: Full body strength','Sat: 10km run','Sun: Active recovery']
  },
  muscle:{
    beginner:['Mon: 3×10 pushups + 3×12 squats','Tue: Rest','Wed: 3×8 pullups + 3×15 lunges','Thu: Rest','Fri: 3×12 dips + 3×20 squats','Sat: Core 3×15','Sun: Rest'],
    intermediate:['Mon: Chest + Triceps 4 sets','Tue: Back + Biceps 4 sets','Wed: Legs 5×20','Thu: Shoulders + Core','Fri: Full body compound','Sat: Light cardio','Sun: Rest'],
    advanced:['Mon: Chest 5×15 + Shoulders','Tue: Back 6×10 + Core','Wed: Legs 6×20','Thu: Arms + HIIT','Fri: Heavy compound','Sat: Olympic lifts','Sun: Rest']
  },
  endurance:{
    beginner:['Mon: 20min jog','Tue: 30 jumping jacks × 3','Wed: Walk/run intervals','Thu: Rest','Fri: 30min light jog','Sat: Circuit 20min','Sun: Rest'],
    intermediate:['Mon: 5km','Tue: HIIT 30min','Wed: 6km tempo','Thu: Cross-train','Fri: 8km easy','Sat: Long run 10km','Sun: Rest'],
    advanced:['Mon: 10km','Tue: Speed 8×400m','Wed: 12km tempo','Thu: Cross-train + strength','Fri: 15km','Sat: 20km long run','Sun: Active recovery']
  },
  flexibility:{
    beginner:['Mon: 20min yoga','Tue: Hip flexor 15min','Wed: Rest','Thu: Full body stretch 20min','Fri: Yoga 25min','Sat: Foam roll','Sun: Rest'],
    intermediate:['Mon: Vinyasa 45min','Tue: Mobility 30min','Wed: Pilates 40min','Thu: Deep stretch','Fri: Power yoga 50min','Sat: Yin yoga 60min','Sun: Rest'],
    advanced:['Mon: Advanced yoga 60min','Tue: Gymnastics mobility','Wed: Flexibility strength','Thu: Deep tissue 45min','Fri: Advanced pilates','Sat: Aerial work','Sun: Restorative']
  },
  general:{
    beginner:['Mon: 20min walk + basics','Tue: Rest','Wed: 30min light','Thu: Rest','Fri: Full body light','Sat: Outdoor activity','Sun: Rest'],
    intermediate:['Mon: Strength 40min','Tue: Cardio 30min','Wed: Full body circuit','Thu: Active rest','Fri: HIIT combo','Sat: Outdoor sport','Sun: Rest'],
    advanced:['Mon: Heavy strength + 20min cardio','Tue: HIIT 45min','Wed: Sport training','Thu: Skill + mobility','Fri: Compound + sprint','Sat: Competition prep','Sun: Rest']
  }
};

// ── NPC COMPETITORS ─────────────────────────────────────
// stepsPerHr = base steps per active hour; calPerHr = base calories per hour
const NPC_COMPETITORS = [
  {id:'alex',  name:'Alex Chen',    av:'AC', color:'#3b82f6', stepsPerHr:480, calPerHr:32},
  {id:'priya', name:'Priya Patel',  av:'PP', color:'#a855f7', stepsPerHr:540, calPerHr:36},
  {id:'ravi',  name:'Ravi Kumar',   av:'RK', color:'#ff6b47', stepsPerHr:360, calPerHr:22},
  {id:'sarah', name:'Sarah Kim',    av:'SK', color:'#47ffb8', stepsPerHr:620, calPerHr:42},
  {id:'marco', name:'Marco Silva',  av:'MS', color:'#ffd700', stepsPerHr:290, calPerHr:18},
  {id:'aisha', name:'Aisha Johnson',av:'AJ', color:'#ff4757', stepsPerHr:510, calPerHr:34},
  {id:'tom',   name:'Tom Hughes',   av:'TH', color:'#00d2ff', stepsPerHr:400, calPerHr:26},
  {id:'mei',   name:'Mei Wang',     av:'MW', color:'#4ade80', stepsPerHr:570, calPerHr:38},
];

// Seeded random (consistent per day per NPC)
function seededRand(seed) {
  const x = Math.sin(seed + 1) * 10000;
  return x - Math.floor(x);
}

function dateSeed() {
  const d = new Date();
  return d.getFullYear() * 10000 + d.getMonth() * 100 + d.getDate();
}

// Get NPC's stats for a given time period
function npcStats(npc, type, period) {
  const now = new Date();
  const hoursToday = now.getHours() + now.getMinutes() / 60;
  const npcSeed = dateSeed() * 17 + npc.id.charCodeAt(0);

  if (period === 'today') {
    const v = (type === 'steps') ? npc.stepsPerHr : npc.calPerHr;
    const variance = 0.80 + seededRand(npcSeed) * 0.40; // 0.80–1.20
    return Math.round(v * hoursToday * variance);
  }
  if (period === 'week') {
    let total = 0;
    for (let d = 0; d < 7; d++) {
      const seed2 = (dateSeed() - d) * 17 + npc.id.charCodeAt(0);
      const hrs = d === 0 ? hoursToday : 14 + seededRand(seed2) * 4; // 14–18 active hrs on past days
      const v = (type === 'steps') ? npc.stepsPerHr : npc.calPerHr;
      const variance = 0.75 + seededRand(seed2 + 1) * 0.50;
      total += Math.round(v * hrs * variance);
    }
    return total;
  }
  // alltime — accumulated over "months" (simulated)
  const seed3 = npcSeed + 9999;
  const v = (type === 'steps') ? npc.stepsPerHr : npc.calPerHr;
  const base = v * 14 * 30; // ~30 days average
  return Math.round(base * (0.8 + seededRand(seed3) * 0.4));
}

// Get NPC's challenge progress given elapsed hours
function npcChallengeProgress(npc, type, elapsedHours) {
  const v = (type === 'steps') ? npc.stepsPerHr : npc.calPerHr;
  const seed = dateSeed() * 31 + npc.id.charCodeAt(0);
  const variance = 0.80 + seededRand(seed) * 0.40;
  return Math.max(0, Math.round(v * elapsedHours * variance));
}

// ── APP STATE ────────────────────────────────────────────
let users = JSON.parse(localStorage.getItem('fq_users') || '{}');
let currentUser = null;
let timerInterval = null, timerSeconds = 0, timerRunning = false;
let sessionReps = 0, sessionExercise = null, repSpeedBucket = [];
let selectedGoal = 'weight_loss', selectedFLevel = 'beginner';
let stepCount = 0;

// Competition state
let competeType   = 'steps';   // 'steps' | 'calories'
let competePeriod = 'today';   // 'today' | 'week' | 'alltime'
let newChallengeType     = 'steps';
let newChallengeDuration = 24;
let newChallengeTarget   = 10000;
let newChallengeOppId    = null;
let challengeRefreshTimer = null;

function getUser()  { return users[currentUser]; }
function saveUsers(){ localStorage.setItem('fq_users', JSON.stringify(users)); }
function getToday() { return new Date().toISOString().split('T')[0]; }

function checkStreak(u) {
  const today = getToday(), yesterday = new Date(Date.now()-86400000).toISOString().split('T')[0];
  if (!u.lastWorkoutDate) return;
  if (u.lastWorkoutDate !== today && u.lastWorkoutDate !== yesterday) u.streak = 0;
}

// ══════════════════════════════════════════
// AUTH
// ══════════════════════════════════════════
function switchTab(t) {
  document.querySelectorAll('.tab-btn').forEach((b,i)=>b.classList.toggle('active',(i===0&&t==='login')||(i===1&&t==='signup')));
  document.getElementById('form-login').classList.toggle('active',t==='login');
  document.getElementById('form-signup').classList.toggle('active',t==='signup');
}

function doLogin() {
  const email = document.getElementById('login-email').value.trim();
  const pass  = document.getElementById('login-pass').value;
  if (!email||!pass) return showToast('Please fill all fields');
  const key = email.toLowerCase();
  if (!users[key]||users[key].password!==pass) return showToast('Invalid email or password');
  currentUser = key;
  localStorage.setItem('fq_current', key);
  launchApp();
}

function doSignup() {
  const name  = document.getElementById('signup-name').value.trim();
  const email = document.getElementById('signup-email').value.trim();
  const pass  = document.getElementById('signup-pass').value;
  const goal  = document.getElementById('signup-goal').value;
  const level = document.getElementById('signup-level').value;
  if (!name||!email||!pass) return showToast('Please fill all fields');
  if (pass.length<6) return showToast('Password must be 6+ characters');
  const key = email.toLowerCase();
  if (users[key]) return showToast('Email already registered');
  users[key] = {
    name, email:key, password:pass, goal:goal||'general', level:level||'beginner',
    workouts:0, points:0, streak:0, bestStreak:0,
    lastWorkoutDate:null, totalReps:0, calories:0,
    challenges:0, challengeDoneToday:false, challengeDateToday:'',
    weeklyData:[0,0,0,0,0,0,0], exerciseCounts:{},
    steps:0, stepDate:'', reminders:{workout:false,streak:false},
    // competition fields
    compWins:0, compLosses:0, winStreak:0, bestWinStreak:0,
    stepRankOnes:0, calRankOnes:0,
    activeChallenges:[], challengeHistory:[]
  };
  saveUsers();
  currentUser = key;
  localStorage.setItem('fq_current', key);
  launchApp();
}

function doLogout() {
  stopTimer(true);
  if (challengeRefreshTimer) clearInterval(challengeRefreshTimer);
  currentUser = null;
  localStorage.removeItem('fq_current');
  document.getElementById('screen-app').classList.remove('active');
  document.getElementById('screen-login').classList.add('active');
  showToast('Logged out. See you tomorrow!');
}

// ══════════════════════════════════════════
// APP LAUNCH
// ══════════════════════════════════════════
function launchApp() {
  const u = getUser();
  checkStreak(u);
  if (u.stepDate !== getToday()) { u.steps=0; u.stepDate=getToday(); }
  if (!u.activeChallenges)  u.activeChallenges = [];
  if (!u.challengeHistory)  u.challengeHistory = [];
  if (!u.compWins)          u.compWins = 0;
  if (!u.compLosses)        u.compLosses = 0;
  if (!u.winStreak)         u.winStreak = 0;
  if (!u.bestWinStreak)     u.bestWinStreak = 0;
  if (!u.stepRankOnes)      u.stepRankOnes = 0;
  if (!u.calRankOnes)       u.calRankOnes = 0;
  saveUsers();

  document.getElementById('screen-login').classList.remove('active');
  document.getElementById('screen-app').classList.add('active');

  const initials = u.name.split(' ').map(n=>n[0]).join('').toUpperCase().slice(0,2);
  document.getElementById('nav-avatar').textContent = initials;
  document.getElementById('nav-username').textContent = u.name.split(' ')[0];
  document.getElementById('home-name').innerHTML = u.name.toUpperCase().split(' ')[0]+' <span>💪</span>';

  // Resolve any expired challenges on login
  resolveExpiredChallenges();

  buildExerciseGrid();
  updateChallenge();
  refreshUI();
  startStepCounter();
  refreshCompeteUI();

  // Auto-refresh challenge timers every 60s
  if (challengeRefreshTimer) clearInterval(challengeRefreshTimer);
  challengeRefreshTimer = setInterval(() => {
    resolveExpiredChallenges();
    if (document.getElementById('page-compete').style.display !== 'none') refreshCompeteUI();
    updateHomeCompSnippet();
  }, 60000);

  showPage('home');
}

// ══════════════════════════════════════════
// UI REFRESH
// ══════════════════════════════════════════
function refreshUI() {
  const u = getUser();
  if (!u) return;

  document.getElementById('stat-streak').textContent  = u.streak+'🔥';
  document.getElementById('stat-workouts').textContent = u.workouts;
  document.getElementById('stat-points').textContent   = u.points;

  let lvIdx = 0;
  for (let i=LEVELS.length-1;i>=0;i--) { if(u.points>=LEVELS[i].xp){lvIdx=i;break;} }
  const nextXP = LEVELS[lvIdx+1]?LEVELS[lvIdx+1].xp:LEVELS[lvIdx].xp;
  const prevXP = LEVELS[lvIdx].xp;
  const pct = lvIdx+1<LEVELS.length ? Math.round(((u.points-prevXP)/(nextXP-prevXP))*100) : 100;
  document.getElementById('level-name').textContent = 'Level '+(lvIdx+1)+' — '+LEVELS[lvIdx].name;
  document.getElementById('level-xp').textContent   = u.points+' / '+nextXP+' XP';
  document.getElementById('level-fill').style.width = pct+'%';

  document.getElementById('prog-total').textContent       = u.workouts;
  document.getElementById('prog-streak-disp').textContent = '🔥 '+u.streak+' day streak';
  document.getElementById('prog-best-streak').textContent = u.bestStreak;
  document.getElementById('prog-total-reps').textContent  = u.totalReps;
  document.getElementById('prog-calories').textContent    = Math.round(u.calories);

  buildWeekChart(u); buildBreakdown(u); updateStepUI(u.steps||0); buildBadges(u);
  updateHomeCompSnippet();
}

function buildWeekChart(u) {
  const days=['Mo','Tu','We','Th','Fr','Sa','Su'],ti=(new Date().getDay()+6)%7;
  const data=u.weeklyData||[0,0,0,0,0,0,0],mx=Math.max(...data,1);
  document.getElementById('week-chart').innerHTML=days.map((d,i)=>{
    const h=Math.round((data[i]/mx)*70);
    return `<div class="chart-bar-wrap"><div class="chart-bar${i===ti?' today':''}" style="height:${h}px"></div><div class="chart-label">${d}</div></div>`;
  }).join('');
}

function buildBreakdown(u) {
  const ec=u.exerciseCounts||{};
  const el=document.getElementById('exercise-breakdown');
  if(!Object.keys(ec).length){el.innerHTML='<p style="font-size:0.8rem;color:var(--muted)">No exercises yet. Start a workout!</p>';return;}
  el.innerHTML=Object.entries(ec).sort((a,b)=>b[1]-a[1]).map(([id,reps])=>{
    const ex=EXERCISES.find(e=>e.id===id);
    return `<div style="display:flex;justify-content:space-between;align-items:center;padding:0.6rem 0.85rem;background:var(--card);border:1px solid var(--border);border-radius:10px;margin-bottom:0.5rem;">
      <span>${ex?ex.icon:''} ${ex?ex.name:id}</span>
      <span style="font-family:var(--font-mono);font-size:0.8rem;color:var(--accent2);">${reps} reps</span></div>`;
  }).join('');
}

function buildBadges(u) {
  const html = BADGES.map(b=>{
    const ok=b.req(u);
    return `<div class="badge-item ${ok?'unlocked':'locked'}"><div class="badge-icon">${b.icon}</div><div class="badge-name">${b.name}</div><div class="badge-desc">${b.desc}</div></div>`;
  }).join('');
  ['badges-home','badges-full'].forEach(id=>{const el=document.getElementById(id);if(el)el.innerHTML=html;});
}

function buildExerciseGrid() {
  document.getElementById('exercise-grid').innerHTML = EXERCISES.map(ex=>
    `<div class="ex-card" id="ex-${ex.id}" onclick="selectExercise('${ex.id}')">
      <div class="ex-icon">${ex.icon}</div><div class="ex-name">${ex.name}</div><div class="ex-muscle">${ex.muscle}</div></div>`
  ).join('');
}

// ══════════════════════════════════════════
// PAGES
// ══════════════════════════════════════════
function showPage(name) {
  ['home','workout','compete','progress','profile'].forEach(p=>{
    document.getElementById('page-'+p).style.display = p===name?'block':'none';
    document.getElementById('nav-'+p).classList.toggle('active', p===name);
  });
  if (name==='progress') refreshUI();
  if (name==='compete')  refreshCompeteUI();
}

function goToWorkout() { showPage('workout'); }

// ══════════════════════════════════════════
// WORKOUT TIMER & REPS
// ══════════════════════════════════════════
function startTimer() {
  if (timerRunning) return;
  timerRunning=true; timerSeconds=0;
  document.getElementById('timer-start-btn').textContent='⏸ Running';
  document.getElementById('timer-status').textContent='Session in progress';
  timerInterval=setInterval(()=>{
    timerSeconds++;
    document.getElementById('workout-timer').textContent=
      String(Math.floor(timerSeconds/60)).padStart(2,'0')+':'+String(timerSeconds%60).padStart(2,'0');
  },1000);
}

function stopTimer(s){if(!timerRunning&&!s)return;clearInterval(timerInterval);timerRunning=false;}

function selectExercise(id) {
  sessionExercise=id;
  document.querySelectorAll('.ex-card').forEach(c=>c.classList.remove('selected'));
  document.getElementById('ex-'+id).classList.add('selected');
  const ex=EXERCISES.find(e=>e.id===id);
  document.getElementById('current-exercise-name').textContent=(ex?ex.name:'EXERCISE').toUpperCase();
  document.getElementById('rep-count-w').textContent=sessionReps;
}

function addRep() {
  if(!timerRunning){showToast('Start the timer first!');return;}
  if(!sessionExercise){showToast('Select an exercise first!');return;}
  const now=Date.now();
  repSpeedBucket=repSpeedBucket.filter(t=>now-t<2000); repSpeedBucket.push(now);
  if(repSpeedBucket.length>6){document.getElementById('anticheat-warn').classList.add('show');return;}
  document.getElementById('anticheat-warn').classList.remove('show');
  sessionReps++;
  document.getElementById('rep-count-w').textContent=sessionReps;
}

function resetReps(){sessionReps=0;document.getElementById('rep-count-w').textContent=0;repSpeedBucket=[];}

function endWorkout() {
  if(timerRunning&&timerSeconds<30){showToast('⚠️ Workout too short to save (min 30s)');return;}
  stopTimer(false);
  const u=getUser(), today=getToday(), tidx=(new Date().getDay()+6)%7;
  const yest=new Date(Date.now()-86400000).toISOString().split('T')[0];
  if(u.lastWorkoutDate===today){}
  else if(u.lastWorkoutDate===yest){u.streak++;}
  else{u.streak=1;}
  u.lastWorkoutDate=today;
  if(u.streak>u.bestStreak)u.bestStreak=u.streak;
  u.workouts++;
  const tMin=timerSeconds/60, ex=EXERCISES.find(e=>e.id===sessionExercise);
  const calBurned=Math.round(sessionReps*(ex?ex.cal:0.4)+tMin*3);
  u.calories+=calBurned; u.totalReps+=sessionReps;
  if(sessionExercise){u.exerciseCounts=u.exerciseCounts||{};u.exerciseCounts[sessionExercise]=(u.exerciseCounts[sessionExercise]||0)+sessionReps;}
  if(!u.weeklyData||u.weeklyData.length<7)u.weeklyData=[0,0,0,0,0,0,0];
  u.weeklyData[tidx]++;
  const xp=Math.max(10,Math.round(sessionReps*0.5+tMin*5));
  u.points+=xp;
  saveUsers();
  const mm=String(Math.floor(timerSeconds/60)).padStart(2,'0');
  const ss=String(timerSeconds%60).padStart(2,'0');
  document.getElementById('sum-time').textContent=mm+':'+ss;
  document.getElementById('sum-reps').textContent=sessionReps;
  document.getElementById('sum-cal').textContent=calBurned;
  document.getElementById('sum-xp').textContent='+'+xp+' XP Earned!';
  document.getElementById('summary-modal').classList.add('open');
  timerSeconds=0;sessionReps=0;timerRunning=false;
  document.getElementById('workout-timer').textContent='00:00';
  document.getElementById('rep-count-w').textContent=0;
  document.getElementById('timer-start-btn').textContent='▶ Start';
  document.getElementById('timer-status').textContent='Ready to start';
  refreshUI();
}

function closeSummary(){document.getElementById('summary-modal').classList.remove('open');showPage('home');}

// ══════════════════════════════════════════
// DAILY CHALLENGE
// ══════════════════════════════════════════
function updateChallenge() {
  const u=getUser(), today=getToday();
  const seed=parseInt(today.replace(/-/g,''))%CHALLENGES_DAILY.length;
  const ch=CHALLENGES_DAILY[seed];
  document.getElementById('ch-title').textContent=ch.title;
  document.getElementById('ch-desc').textContent=ch.desc;
  document.getElementById('ch-reward').textContent='+'+ch.reward+' XP';
  if(u.challengeDateToday===today&&u.challengeDoneToday){
    const btn=document.getElementById('ch-btn');
    btn.textContent='✅ Completed!';btn.disabled=true;
    btn.style.color='var(--accent2)';btn.style.borderColor='var(--accent2)';
  }
}

function completeChallenge() {
  const u=getUser(), today=getToday();
  const seed=parseInt(today.replace(/-/g,''))%CHALLENGES_DAILY.length;
  const ch=CHALLENGES_DAILY[seed];
  if(u.challengeDateToday===today&&u.challengeDoneToday)return;
  u.points+=ch.reward; u.challengeDoneToday=true; u.challengeDateToday=today; u.challenges=(u.challenges||0)+1;
  saveUsers();
  const btn=document.getElementById('ch-btn');
  btn.textContent='✅ Completed!';btn.disabled=true;btn.style.color='var(--accent2)';btn.style.borderColor='var(--accent2)';
  showToast('🎉 Challenge done! +'+ch.reward+' XP');
  refreshUI();
}

// ══════════════════════════════════════════
// STEP COUNTER
// ══════════════════════════════════════════
function updateStepUI(steps) {
  stepCount=steps;
  document.getElementById('step-count').textContent=steps.toLocaleString();
  const pct=Math.min(100,Math.round((steps/10000)*100));
  document.getElementById('step-fill').style.width=pct+'%';
  const msgs=['Walk around to count steps','Keep going!','Halfway there!','Almost at goal!','Goal reached! 🎉'];
  document.getElementById('step-msg').textContent=msgs[pct>=100?4:pct>=75?3:pct>=50?2:pct>=20?1:0]+' '+pct+'%';
}

function startStepCounter() {
  const statusEl=document.getElementById('step-status');
  const u=getUser(); updateStepUI(u.steps||0);
  if(window.DeviceMotionEvent) {
    let accelHistory=[],lastStepTime=0;
    const handle=(e)=>{
      const acc=e.accelerationIncludingGravity;
      if(!acc||acc.x===null)return;
      const mag=Math.sqrt(acc.x**2+acc.y**2+acc.z**2);
      accelHistory.push(mag);if(accelHistory.length>20)accelHistory.shift();
      const avg=accelHistory.reduce((a,b)=>a+b,0)/accelHistory.length;
      const now=Date.now();
      if(Math.abs(mag-avg)>12&&now-lastStepTime>300){
        lastStepTime=now;const u2=getUser();if(!u2)return;
        u2.steps=(u2.steps||0)+1;saveUsers();updateStepUI(u2.steps);statusEl.textContent='Counting...';
        // check rank after step update
        checkRankAchievements();
      }
    };
    if(typeof DeviceMotionEvent.requestPermission==='function'){
      statusEl.textContent='Tap to enable';statusEl.style.cursor='pointer';
      statusEl.onclick=()=>DeviceMotionEvent.requestPermission().then(s=>{if(s==='granted'){window.addEventListener('devicemotion',handle);statusEl.textContent='Active';}});
    } else {window.addEventListener('devicemotion',handle);statusEl.textContent='Active';}
  } else {
    statusEl.textContent='Simulated';
    setInterval(()=>{
      const u2=getUser();if(!u2||!document.getElementById('screen-app').classList.contains('active'))return;
      u2.steps=(u2.steps||0)+Math.floor(Math.random()*3);saveUsers();updateStepUI(u2.steps);
    },3000);
  }
}

// ══════════════════════════════════════════
// PERSONALIZATION
// ══════════════════════════════════════════
function selectOpt(type,val,el){
  if(type==='goal'){selectedGoal=val;document.querySelectorAll('#goal-opts .plan-opt').forEach(o=>o.classList.remove('selected'));}
  else{selectedFLevel=val;document.querySelectorAll('#level-opts .plan-opt').forEach(o=>o.classList.remove('selected'));}
  el.classList.add('selected');
}

function generatePlan(){
  const plan=(PLANS[selectedGoal]||PLANS.general)[selectedFLevel]||PLANS.general.beginner;
  const el=document.getElementById('generated-plan');
  el.innerHTML=`<h4>YOUR CUSTOM PLAN</h4><div style="color:var(--muted);font-size:0.75rem;margin-bottom:0.75rem;">${selectedGoal.replace('_',' ').toUpperCase()} · ${selectedFLevel.toUpperCase()}</div>`+
    plan.map(d=>`<div style="padding:0.35rem 0;border-bottom:1px solid var(--border);">📅 ${d}</div>`).join('');
  el.classList.add('show');
  const u=getUser();u.goal=selectedGoal;u.level=selectedFLevel;saveUsers();
  showToast('✅ Plan generated!');
}

function toggleReminder(type){
  const checked=document.getElementById('rem-'+type).checked;
  const track=document.getElementById('rem-'+type+'-track'),thumb=document.getElementById('rem-'+type+'-thumb');
  if(checked){track.style.background='rgba(232,255,71,0.2)';track.style.borderColor='var(--accent)';thumb.style.background='var(--accent)';thumb.style.transform='translateX(20px)';}
  else{track.style.background='var(--bg3)';track.style.borderColor='var(--border2)';thumb.style.background='var(--muted)';thumb.style.transform='translateX(0)';}
  const u=getUser();u.reminders=u.reminders||{};u.reminders[type]=checked;saveUsers();
  showToast(checked?'🔔 Reminder enabled':'🔕 Reminder off');
}

// ══════════════════════════════════════════════════════════
// ══  COMPETITION SYSTEM  ══════════════════════════════════
// ══════════════════════════════════════════════════════════

function setCompeteType(type) {
  competeType=type;
  document.getElementById('ctype-steps').classList.toggle('active',type==='steps');
  document.getElementById('ctype-calories').classList.toggle('active',type==='calories');
  renderLeaderboard();
}

function setCompetePeriod(period) {
  competePeriod=period;
  ['today','week','alltime'].forEach(p=>document.getElementById('period-'+p).classList.toggle('active',p===period));
  renderLeaderboard();
}

// Build full competitor list including the user, sorted by value
function buildRankedList(type, period) {
  const u = getUser();
  let userVal = 0;
  if (type === 'steps') {
    userVal = period === 'today' ? (u.steps||0) : period === 'week' ? (u.steps||0)*3 : (u.steps||0)*30; // rough estimates for non-today
  } else {
    userVal = period === 'today' ? Math.round(u.calories) : period === 'week' ? Math.round(u.calories)*3 : Math.round(u.calories)*30;
  }

  const entries = NPC_COMPETITORS.map(npc=>({
    id: npc.id, name: npc.name, av: npc.av, color: npc.color,
    val: npcStats(npc, type, period), isMe: false
  }));
  entries.push({id:'me', name: u.name+' (You)', av: u.name.split(' ').map(n=>n[0]).join('').toUpperCase().slice(0,2), color:'#e8ff47', val: userVal, isMe: true});
  entries.sort((a,b)=>b.val-a.val);
  return entries;
}

function renderLeaderboard() {
  const list = buildRankedList(competeType, competePeriod);
  const max  = list[0]?.val || 1;
  const unit = competeType === 'steps' ? 'steps' : 'kcal';
  const myIdx = list.findIndex(e=>e.isMe);

  // Update rank banner
  const rankNum = myIdx + 1;
  document.getElementById('rank-num').textContent = '#'+rankNum;
  const me = list[myIdx];
  document.getElementById('rank-text').textContent = fmtVal(me.val, competeType)+' '+unit+' · #'+rankNum+' of '+(list.length);
  const change = myIdx === 0 ? '🏆 You are leading!' : myIdx <= 2 ? '🔥 Top 3 — keep pushing!' : `${list.length - rankNum} behind you`;
  document.getElementById('rank-change').textContent = change;
  document.getElementById('rank-change').className = 'rank-change '+(myIdx===0?'up':'same');

  // Update home badge
  document.getElementById('home-rank-badge').textContent = '#'+rankNum+' '+unit;

  // Check rank achievements
  const u = getUser();
  if (myIdx === 0 && competePeriod === 'today') {
    if (competeType === 'steps' && !u._stepRankChecked) { u.stepRankOnes=(u.stepRankOnes||0)+1; u._stepRankChecked=true; saveUsers(); }
    if (competeType === 'calories' && !u._calRankChecked) { u.calRankOnes=(u.calRankOnes||0)+1; u._calRankChecked=true; saveUsers(); }
  }

  // Render rows
  const rankClasses = ['r1','r2','r3'];
  document.getElementById('leaderboard-list').innerHTML = list.map((e,i)=>`
    <div class="lb-row ${e.isMe?'me':''}">
      <div class="lb-rank ${e.isMe?'rme':rankClasses[i]||''}">${i+1}</div>
      <div class="lb-avatar" style="background:${e.color}">${e.av}</div>
      <div class="lb-info">
        <div class="lb-name ${e.isMe?'me-name':''}">${e.name}</div>
        <div class="lb-sub">${competePeriod==='today'?'Today':competePeriod==='week'?'This week':'All time'}</div>
      </div>
      <div class="lb-stat">
        <div class="lb-val" style="color:${e.color}">${fmtVal(e.val,competeType)}</div>
        <div class="lb-unit">${unit}</div>
      </div>
      ${!e.isMe ? `<button class="duel-btn" onclick="quickDuel('${e.id}')">⚔ Duel</button>` : ''}
      <div class="lb-bar-wrap"><div class="lb-bar" style="width:${Math.round((e.val/max)*100)}%;background:${e.color}"></div></div>
    </div>`).join('');
}

function fmtVal(v, type) {
  if (type === 'steps') return v >= 1000 ? (v/1000).toFixed(1)+'K' : String(v);
  return String(Math.round(v));
}

// ══════════════════════════════════════════
// CHALLENGE CREATION
// ══════════════════════════════════════════
function openCreateChallenge() {
  const u = getUser();
  if ((u.activeChallenges||[]).length >= 3) {
    showToast('Max 3 active challenges at once!'); return;
  }
  // Reset form state
  newChallengeType     = 'steps';
  newChallengeDuration = 24;
  newChallengeTarget   = 10000;
  newChallengeOppId    = null;
  setChallengeType('steps');
  setDuration(24);
  document.getElementById('cs-target').value = 10000;
  renderOppGrid();
  document.getElementById('create-challenge-modal').classList.add('open');
}

function setChallengeType(type) {
  newChallengeType = type;
  document.getElementById('cs-steps').classList.toggle('active', type==='steps');
  document.getElementById('cs-calories').classList.toggle('active', type==='calories');
  document.getElementById('cs-unit-label').textContent = type==='steps'?'steps':'calories (kcal)';
  document.getElementById('cs-target').placeholder = type==='steps'?'10000':'500';
  document.getElementById('cs-target').value = type==='steps'?10000:500;
  newChallengeTarget = type==='steps'?10000:500;
  renderOppGrid();
}

function setDuration(hrs) {
  newChallengeDuration = hrs;
  ['24','48','168'].forEach(h=>document.getElementById('dur-'+h).classList.toggle('active',hrs===parseInt(h)));
}

function setQuickTarget(v) {
  newChallengeTarget = v;
  document.getElementById('cs-target').value = v;
}

function renderOppGrid() {
  const u = getUser();
  const activeOppIds = (u.activeChallenges||[]).map(c=>c.oppId);
  document.getElementById('opp-select-grid').innerHTML = NPC_COMPETITORS.map(npc=>{
    const todayVal = npcStats(npc, newChallengeType, 'today');
    const unit = newChallengeType==='steps'?'steps today':'kcal today';
    const busy = activeOppIds.includes(npc.id);
    return `<button class="opp-btn${newChallengeOppId===npc.id?' active':''}${busy?' disabled':''}"
      onclick="${busy?'showToast(\'Already in a challenge with this opponent\')':'selectOpp(\''+npc.id+'\')'}">
      <div class="opp-av" style="background:${npc.color}">${npc.av}</div>
      <div><div class="opp-name-sm">${npc.name.split(' ')[0]}</div><div class="opp-stat-sm">${fmtVal(todayVal,newChallengeType)} ${unit}</div></div>
    </button>`;
  }).join('');
}

function selectOpp(id) {
  newChallengeOppId = id;
  document.querySelectorAll('.opp-btn').forEach(b=>b.classList.remove('active'));
  renderOppGrid();
}

function startChallenge() {
  if (!newChallengeOppId) { showToast('Pick an opponent first!'); return; }
  const targetVal = parseInt(document.getElementById('cs-target').value) || newChallengeTarget;
  if (targetVal < 100) { showToast('Target too low!'); return; }

  const u = getUser();
  const npc = NPC_COMPETITORS.find(n=>n.id===newChallengeOppId);
  const challenge = {
    id: Date.now()+'',
    type: newChallengeType,
    target: targetVal,
    durationHrs: newChallengeDuration,
    oppId: newChallengeOppId,
    oppName: npc.name,
    oppColor: npc.color,
    oppAv: npc.av,
    startTime: Date.now(),
    userValAtStart: newChallengeType==='steps' ? (u.steps||0) : Math.round(u.calories),
    status: 'active'
  };

  u.activeChallenges = u.activeChallenges || [];
  u.activeChallenges.push(challenge);
  saveUsers();
  closeModal('create-challenge-modal');
  showToast('⚔️ Challenge started! vs '+npc.name);
  refreshCompeteUI();
}

function quickDuel(npcId) {
  const u = getUser();
  if ((u.activeChallenges||[]).length>=3){showToast('Max 3 active challenges!');return;}
  if ((u.activeChallenges||[]).some(c=>c.oppId===npcId)){showToast('Already dueling this opponent!');return;}
  newChallengeOppId = npcId;
  newChallengeType = competeType;
  newChallengeDuration = 24;
  newChallengeTarget = competeType==='steps' ? 10000 : 500;
  document.getElementById('cs-target').value = newChallengeTarget;
  setChallengeType(competeType);
  setDuration(24);
  renderOppGrid();
  document.getElementById('create-challenge-modal').classList.add('open');
}

// ══════════════════════════════════════════
// CHALLENGE RENDERING
// ══════════════════════════════════════════
function renderActiveChallenges() {
  const u = getUser();
  const challenges = u.activeChallenges || [];
  const el = document.getElementById('active-challenges-list');
  document.getElementById('active-ch-count').textContent = challenges.length+' / 3';

  if (!challenges.length) {
    el.innerHTML = '<div style="text-align:center;padding:1.25rem;color:var(--muted);font-size:0.8rem;background:var(--card);border:1px solid var(--border);border-radius:14px;">No active challenges. Start one below! ⚔️</div>';
    return;
  }

  el.innerHTML = challenges.map(ch=>{
    const npc = NPC_COMPETITORS.find(n=>n.id===ch.oppId);
    const elapsed = (Date.now() - ch.startTime) / 3600000; // hours
    const remaining = Math.max(0, ch.durationHrs - elapsed);
    const remStr = remaining < 1 ? Math.round(remaining*60)+'m left' : Math.round(remaining)+'h left';

    // User progress since challenge start
    const currentUserVal = ch.type==='steps' ? (u.steps||0) : Math.round(u.calories);
    const userProgress = Math.max(0, currentUserVal - ch.userValAtStart);

    // NPC progress
    const npcProgress = npcChallengeProgress(npc, ch.type, elapsed);

    const maxProg = Math.max(ch.target, userProgress, npcProgress, 1);
    const userPct = Math.round((userProgress/maxProg)*100);
    const npcPct  = Math.round((npcProgress/maxProg)*100);
    const targetPct = Math.round((ch.target/maxProg)*100);

    const diff = userProgress - npcProgress;
    const statusText = diff > 0 ? `🟢 Leading by ${fmtVal(diff,ch.type)}` : diff < 0 ? `🔴 Behind by ${fmtVal(Math.abs(diff),ch.type)}` : '🟡 Tied!';
    const statusClass = diff > 0 ? 'winning' : diff < 0 ? 'losing' : 'tied';
    const unit = ch.type==='steps'?'steps':'kcal';

    return `<div class="active-challenge-card">
      <div class="ac-header">
        <span class="ac-vs">VS</span>
        <div class="lb-avatar" style="background:${ch.oppColor};width:28px;height:28px;font-size:0.62rem">${ch.oppAv}</div>
        <span class="ac-opp-name">${ch.oppName}</span>
        <span class="ac-type-badge ${ch.type}">${ch.type==='steps'?'👟 Steps':'🔥 Calories'}</span>
        <span class="ac-time">${remStr}</span>
      </div>
      <div class="race-row">
        <div class="race-avatar" style="background:#e8ff47">YOU</div>
        <div class="race-name" style="font-size:0.7rem">You</div>
        <div class="race-bar-wrap"><div class="race-bar" style="width:${userPct}%;background:#e8ff47"></div></div>
        <div class="race-val" style="color:#e8ff47">${fmtVal(userProgress,ch.type)}</div>
      </div>
      <div class="race-row">
        <div class="race-avatar" style="background:${ch.oppColor}">${ch.oppAv}</div>
        <div class="race-name" style="font-size:0.7rem">${ch.oppName.split(' ')[0]}</div>
        <div class="race-bar-wrap"><div class="race-bar" style="width:${npcPct}%;background:${ch.oppColor}"></div></div>
        <div class="race-val" style="color:${ch.oppColor}">${fmtVal(npcProgress,ch.type)}</div>
      </div>
      <div style="font-size:0.64rem;color:var(--muted);margin-top:0.3rem;">Target: ${fmtVal(ch.target,ch.type)} ${unit}</div>
      <div class="ac-status">
        <span class="ac-status-text ${statusClass}">${statusText}</span>
        <button class="ac-abandon-btn" onclick="abandonChallenge('${ch.id}')">Abandon</button>
      </div>
    </div>`;
  }).join('');
}

function renderChallengeHistory() {
  const u = getUser();
  const hist = (u.challengeHistory||[]).slice(-10).reverse();
  const el = document.getElementById('challenge-history');
  if (!hist.length) {
    el.innerHTML = '<div style="text-align:center;padding:1.25rem;color:var(--muted);font-size:0.8rem;">No challenges yet — start competing!</div>';
    return;
  }
  el.innerHTML = hist.map(h=>{
    const icon = h.result==='won'?'✅':h.result==='lost'?'❌':'🤝';
    const date = new Date(h.endTime).toLocaleDateString();
    const unit = h.type==='steps'?'steps':'kcal';
    return `<div class="hist-row">
      <div class="hist-icon">${icon}</div>
      <div class="hist-info">
        <div class="hist-title">${h.result==='won'?'Beat':'Lost to'} ${h.oppName}</div>
        <div class="hist-sub">${h.type==='steps'?'👟':'🔥'} ${fmtVal(h.userVal,h.type)} vs ${fmtVal(h.oppVal,h.type)} ${unit} · ${date}</div>
      </div>
      <div class="hist-xp">${h.result==='won'?'+'+h.xp+' XP':''}</div>
    </div>`;
  }).join('');
}

// ══════════════════════════════════════════
// RESOLVE EXPIRED CHALLENGES
// ══════════════════════════════════════════
function resolveExpiredChallenges() {
  const u = getUser();
  if (!(u.activeChallenges||[]).length) return;
  let changed = false;

  u.activeChallenges = u.activeChallenges.filter(ch=>{
    const elapsed = (Date.now() - ch.startTime) / 3600000;
    if (elapsed < ch.durationHrs) return true; // still active

    // Challenge expired — determine winner
    const currentUserVal = ch.type==='steps' ? (u.steps||0) : Math.round(u.calories);
    const userProgress = Math.max(0, currentUserVal - ch.userValAtStart);
    const npc = NPC_COMPETITORS.find(n=>n.id===ch.oppId);
    const npcProgress = npcChallengeProgress(npc, ch.type, ch.durationHrs);

    let result, xp=0;
    if (userProgress > npcProgress) {
      result='won';xp=50+Math.round(ch.durationHrs/24*30);
      u.compWins=(u.compWins||0)+1;
      u.winStreak=(u.winStreak||0)+1;
      if(u.winStreak>(u.bestWinStreak||0))u.bestWinStreak=u.winStreak;
      u.points=(u.points||0)+xp;
      showResultModal('won', ch.oppName, userProgress, npcProgress, ch.type, xp);
    } else if (npcProgress > userProgress) {
      result='lost';xp=0;
      u.compLosses=(u.compLosses||0)+1;
      u.winStreak=0;
      showResultModal('lost', ch.oppName, userProgress, npcProgress, ch.type, 0);
    } else {
      result='draw';xp=10;u.points=(u.points||0)+xp;
      u.winStreak=0;
      showResultModal('draw', ch.oppName, userProgress, npcProgress, ch.type, xp);
    }

    u.challengeHistory = u.challengeHistory||[];
    u.challengeHistory.push({result,oppName:ch.oppName,oppVal:npcProgress,userVal:userProgress,type:ch.type,xp,endTime:Date.now()});

    changed = true;
    return false; // remove from active
  });

  if (changed) { saveUsers(); refreshUI(); }
}

function abandonChallenge(id) {
  const u = getUser();
  const idx = u.activeChallenges.findIndex(c=>c.id===id);
  if (idx === -1) return;
  const ch = u.activeChallenges.splice(idx,1)[0];
  u.challengeHistory = u.challengeHistory||[];
  u.challengeHistory.push({result:'abandoned',oppName:ch.oppName,oppVal:0,userVal:0,type:ch.type,xp:0,endTime:Date.now()});
  u.winStreak=0;
  saveUsers();
  showToast('Challenge abandoned.');
  refreshCompeteUI();
}

function showResultModal(result, oppName, userVal, oppVal, type, xp) {
  const icons = {won:'🏆',lost:'😤',draw:'🤝'};
  const titles = {won:'YOU WON!',lost:'CLOSE ONE!',draw:"IT'S A DRAW"};
  const subs = {won:'Outstanding effort! Keep dominating!',lost:'They beat you this time. Train harder!',draw:"Perfectly matched. Rematch?"};
  document.getElementById('result-icon').textContent = icons[result];
  document.getElementById('result-title').textContent = titles[result];
  document.getElementById('result-subtitle').textContent = subs[result];
  document.getElementById('rv-you').textContent = fmtVal(userVal,type);
  document.getElementById('rv-opp-name').textContent = oppName.split(' ')[0];
  document.getElementById('rv-opp').textContent = fmtVal(oppVal,type);
  document.getElementById('rv-you').style.color = result==='won'?'var(--accent2)':result==='lost'?'var(--danger)':'var(--gold)';
  document.getElementById('result-xp').textContent = xp>0 ? '+'+xp+' XP Earned!' : 'No XP — try again!';
  document.getElementById('result-xp').style.display = 'block';
  document.getElementById('result-modal').classList.add('open');
}

// ══════════════════════════════════════════
// REFRESH COMPETE PAGE
// ══════════════════════════════════════════
function refreshCompeteUI() {
  renderLeaderboard();
  renderActiveChallenges();
  renderChallengeHistory();
}

// Home snippet update
function updateHomeCompSnippet() {
  const u = getUser();
  const list = buildRankedList('steps','today');
  const myRank = list.findIndex(e=>e.isMe)+1;
  document.getElementById('home-rank-badge').textContent = '#'+myRank+' Steps';
  const active = (u.activeChallenges||[]);
  if (active.length) {
    const ch = active[0];
    const elapsed = (Date.now()-ch.startTime)/3600000;
    const userProg = Math.max(0,(ch.type==='steps'?(u.steps||0):Math.round(u.calories))-ch.userValAtStart);
    const npc = NPC_COMPETITORS.find(n=>n.id===ch.oppId);
    const npcProg = npcChallengeProgress(npc,ch.type,elapsed);
    const diff = userProg-npcProg;
    document.getElementById('home-comp-preview').textContent =
      `⚔️ vs ${ch.oppName.split(' ')[0]}: ${diff>=0?'Leading':'Behind'} by ${fmtVal(Math.abs(diff),ch.type)} ${ch.type==='steps'?'steps':'kcal'}`;
  } else {
    document.getElementById('home-comp-preview').textContent = `You're ranked #${myRank} in steps today · Tap to compete`;
  }
}

function checkRankAchievements() {
  const u = getUser();
  const list = buildRankedList('steps','today');
  if (list[0]?.isMe && !u._stepRankChecked) { u.stepRankOnes=(u.stepRankOnes||0)+1; u._stepRankChecked=true; saveUsers(); }
}

// ══════════════════════════════════════════
// MODAL HELPERS
// ══════════════════════════════════════════
function openModal(id)  { document.getElementById(id).classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }

// ══════════════════════════════════════════
// TOAST
// ══════════════════════════════════════════
let toastTimer=null;
function showToast(msg){
  const el=document.getElementById('toast');el.textContent=msg;el.classList.add('show');
  clearTimeout(toastTimer);toastTimer=setTimeout(()=>el.classList.remove('show'),2800);
}

// ══════════════════════════════════════════
// AUTO-LOGIN
// ══════════════════════════════════════════
const saved = localStorage.getItem('fq_current');
if (saved && users[saved]) { currentUser=saved; launchApp(); }
</script>
</body>
</html>
