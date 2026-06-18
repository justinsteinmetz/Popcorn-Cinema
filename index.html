import { useState, useEffect } from "react";

const FILMS = [
  { id: "judas", title: "Judas and the Black Messiah", day: 1, year: 2021, director: "Shaka King", accent: "#c0392b" },
  { id: "noother", title: "No Other Choice", day: 1, year: 2025, director: "Romain Gavras", accent: "#8e44ad" },
  { id: "sinners", title: "Sinners", day: 2, year: 2025, director: "Ryan Coogler", accent: "#e67e22" },
  { id: "sorry", title: "Sorry to Bother You", day: 2, year: 2018, director: "Boots Riley", accent: "#e74c3c" },
  { id: "christophers", title: "The Christophers", day: 3, year: 2025, director: "Chris Andrews", accent: "#2980b9" },
  { id: "favourite", title: "The Favourite", day: 3, year: 2018, director: "Yorgos Lanthimos", accent: "#7f8c8d" },
];

const STORAGE_KEY = "popcorn-cinema-2026";
const DAY_DATES = { 1: "22 June", 2: "23 June", 3: "24 June" };

function getCurrentFestivalDay() {
  const now = new Date();
  const y = now.getFullYear(), m = now.getMonth(), d = now.getDate();
  if (y > 2026 || (y === 2026 && m > 5)) return 3;
  if (y === 2026 && m === 5) {
    if (d >= 24) return 3;
    if (d === 23) return 2;
    if (d === 22) return 1;
  }
  return 0;
}

function getAvg(submissions, film) {
  const subs = submissions.filter(s => s.dayRatings?.[film.day]?.ratings?.[film.id] != null);
  if (!subs.length) return { avg: null, count: 0 };
  const avg = subs.reduce((a, s) => a + s.dayRatings[film.day].ratings[film.id], 0) / subs.length;
  return { avg, count: subs.length };
}

// Reconstruct which days a named user has already submitted
function getSubmittedDays(submissions, name) {
  if (!name) return {};
  const entry = submissions.find(s => s.name.toLowerCase() === name.toLowerCase());
  if (!entry) return {};
  const result = {};
  [1, 2, 3].forEach(day => {
    const dr = entry.dayRatings?.[day];
    if (dr && FILMS.filter(f => f.day === day).every(f => dr.ratings?.[f.id] != null)) {
      result[day] = true;
    }
  });
  return result;
}

const css = `
  @import url('https://fonts.googleapis.com/css2?family=Anton&family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&display=swap');
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { background: #080808; }
  .scratch { position: fixed; top: 0; bottom: 0; width: 1px; background: rgba(255,255,255,0.025); pointer-events: none; z-index: 0; }
  .scratch-1 { left: 33%; } .scratch-2 { left: 71%; }
  .grain { position: fixed; top: 0; left: 0; right: 0; bottom: 0; pointer-events: none; z-index: 0; opacity: 0.055;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
    background-size: 200px 200px; }
  .app { position: relative; z-index: 1; max-width: 720px; margin: 0 auto; padding: 0 0 80px; }
  .hero { padding: 48px 24px 32px; border-bottom: 1px solid #141414; }
  .eyebrow { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.25em; text-transform: uppercase; color: #333; margin-bottom: 16px; }
  .festival-title { font-family: 'Anton', sans-serif; font-size: clamp(64px, 14vw, 120px); line-height: 0.9; color: #fff; letter-spacing: -0.01em; text-transform: uppercase; }
  .festival-title .cinema { color: transparent; -webkit-text-stroke: 1px #fff; }
  .byline { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 13px; color: #333; margin-top: 14px; line-height: 1.6; }
  .nav { display: flex; border-bottom: 1px solid #141414; padding: 0 24px; position: sticky; top: 0; background: #080808; z-index: 10; }
  .nav-btn { background: none; border: none; border-bottom: 2px solid transparent; color: #333; font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase; padding: 16px 20px 14px; cursor: pointer; transition: color 0.15s; margin-bottom: -1px; }
  .nav-btn:hover { color: #666; } .nav-btn.active { color: #fff; border-bottom-color: #fff; }
  .content { padding: 40px 24px 0; }
  .day-block { margin-bottom: 48px; }
  .day-label { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.25em; text-transform: uppercase; color: #222; display: flex; align-items: center; gap: 16px; margin-bottom: 20px; }
  .day-label::after { content: ''; flex: 1; height: 1px; background: #141414; }
  .submitted-badge { color: #2ecc71; font-size: 9px; letter-spacing: 0.2em; }
  .locked-badge { color: #1e1e1e; font-size: 9px; }
  .film-card { border: 1px solid #141414; margin-bottom: 2px; position: relative; overflow: hidden; transition: border-color 0.2s; }
  .film-card:hover { border-color: #222; } .film-card.locked { opacity: 0.25; pointer-events: none; }
  .film-card-accent { position: absolute; left: 0; top: 0; bottom: 0; width: 2px; }
  .film-card-inner { padding: 20px 20px 20px 28px; }
  .film-title { font-family: 'DM Serif Display', serif; font-size: 20px; color: #eee; margin-bottom: 4px; line-height: 1.2; }
  .film-meta { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.12em; color: #2a2a2a; text-transform: uppercase; margin-bottom: 16px; }
  .dots { display: flex; gap: 5px; align-items: center; flex-wrap: wrap; margin-bottom: 4px; }
  .dot { width: 22px; height: 22px; border-radius: 50%; border: none; cursor: pointer; background: #141414; transition: background 0.1s, transform 0.1s; flex-shrink: 0; }
  .dot:hover { transform: scale(1.15); } .dot:disabled { cursor: default; } .dot:disabled:hover { transform: none; }
  .dot-score { font-family: 'Anton', sans-serif; font-size: 13px; letter-spacing: 0.05em; margin-left: 8px; }
  .review-input { display: block; width: 100%; margin-top: 14px; background: #0c0c0c; border: 1px solid #141414; color: #888; padding: 10px 14px; font-family: 'DM Serif Display', serif; font-style: italic; font-size: 14px; line-height: 1.7; resize: vertical; outline: none; transition: border-color 0.2s; }
  .review-input:focus { border-color: #2a2a2a; color: #aaa; } .review-input::placeholder { color: #1e1e1e; }
  .submitted-review { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 13px; color: #333; margin-top: 12px; line-height: 1.7; padding-left: 12px; border-left: 1px solid #1e1e1e; }
  .film-avg-inline { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.12em; text-transform: uppercase; margin-top: 12px; color: #333; }
  .submit-btn { display: block; margin-top: 20px; background: none; border: 1px solid #222; color: #333; font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.25em; text-transform: uppercase; padding: 12px 24px; cursor: default; transition: all 0.2s; }
  .submit-btn.ready { border-color: #fff; color: #fff; cursor: pointer; }
  .submit-btn.ready:hover { background: #fff; color: #080808; }
  .confirm-banner { margin-top: 16px; padding: 16px 20px; border: 1px solid #1a3a1a; background: #0a160a; }
  .confirm-banner-title { font-family: 'Anton', sans-serif; font-size: 16px; color: #2ecc71; letter-spacing: 0.05em; margin-bottom: 4px; }
  .confirm-banner-sub { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 13px; color: #2a5a2a; }
  .name-screen { max-width: 480px; }
  .name-label { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase; color: #333; display: block; margin-bottom: 10px; }
  .name-hint { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 13px; color: #222; margin-bottom: 20px; line-height: 1.6; }
  .name-row { display: flex; gap: 10px; }
  .name-input { flex: 1; background: #0c0c0c; border: 1px solid #1e1e1e; color: #eee; padding: 12px 16px; font-family: 'DM Serif Display', serif; font-size: 16px; outline: none; transition: border-color 0.2s; }
  .name-input:focus { border-color: #333; }
  .name-btn { background: #fff; border: none; color: #080808; font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase; padding: 12px 20px; cursor: pointer; transition: opacity 0.2s; }
  .name-btn:hover { opacity: 0.85; }
  .voting-as { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.15em; color: #333; text-transform: uppercase; margin-bottom: 32px; display: flex; gap: 16px; align-items: center; }
  .voting-as strong { color: #fff; font-weight: 500; }
  .voting-as button { background: none; border: none; color: #222; font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.15em; text-transform: uppercase; cursor: pointer; text-decoration: underline; }
  .intro-text { font-family: 'DM Serif Display', serif; font-size: 15px; color: #444; line-height: 1.8; margin-bottom: 32px; max-width: 440px; }
  .film-row { display: flex; justify-content: space-between; align-items: flex-start; gap: 16px; padding: 20px 0; border-bottom: 1px solid #0e0e0e; cursor: pointer; transition: background 0.15s; }
  .film-row:hover { background: #0d0d0d; margin: 0 -24px; padding: 20px 24px; }
  .film-row-title { font-family: 'DM Serif Display', serif; font-size: 18px; color: #ccc; margin-bottom: 4px; line-height: 1.2; }
  .film-row-meta { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.12em; color: #222; text-transform: uppercase; }
  .big-score { font-family: 'Anton', sans-serif; font-size: 36px; line-height: 1; text-align: right; flex-shrink: 0; }
  .big-score-sub { font-family: 'DM Mono', monospace; font-size: 9px; letter-spacing: 0.1em; color: #222; text-align: right; margin-top: 2px; }
  .reviews-panel { padding: 0 0 24px 0; border-bottom: 1px solid #0e0e0e; }
  .review-item { padding: 16px 0; border-bottom: 1px solid #0e0e0e; }
  .review-item:last-child { border-bottom: none; }
  .review-author { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.15em; text-transform: uppercase; margin-bottom: 6px; display: flex; justify-content: space-between; }
  .review-score { color: #333; }
  .review-text { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 14px; color: #555; line-height: 1.7; }
  .no-reviews { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 14px; color: #1e1e1e; padding: 16px 0; }
  .lb-row { display: flex; align-items: center; gap: 20px; padding: 18px 0; border-bottom: 1px solid #0e0e0e; }
  .lb-rank { font-family: 'Anton', sans-serif; font-size: 28px; color: #1a1a1a; width: 36px; text-align: right; flex-shrink: 0; }
  .lb-rank.gold { color: #fff; }
  .lb-title { font-family: 'DM Serif Display', serif; font-size: 17px; color: #bbb; flex: 1; line-height: 1.2; }
  .lb-day { font-family: 'DM Mono', monospace; font-size: 9px; letter-spacing: 0.12em; color: #222; text-transform: uppercase; margin-top: 3px; }
  .lb-score { font-family: 'Anton', sans-serif; font-size: 32px; flex-shrink: 0; }
  .voters-section { margin-top: 40px; }
  .voters-label { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase; color: #1e1e1e; margin-bottom: 14px; }
  .voter-chip { display: inline-block; border: 1px solid #141414; color: #333; font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; padding: 5px 12px; margin: 0 6px 6px 0; }
  .empty { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 15px; color: #1e1e1e; padding: 32px 0; }
  .locked-screen { font-family: 'DM Serif Display', serif; font-style: italic; font-size: 16px; color: #222; padding: 48px 0; }
  .error-msg { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.12em; color: #8b3a3a; margin-bottom: 10px; text-transform: uppercase; }
`;

function FilmDots({ value, onChange, disabled, accent }) {
  const [hover, setHover] = useState(null);
  const active = hover ?? value ?? 0;
  return (
    <div className="dots">
      {[1,2,3,4,5,6,7,8,9,10].map(n => (
        <button key={n} className="dot" disabled={disabled}
          style={{ background: n <= active ? accent : "#141414" }}
          onClick={() => onChange && onChange(n)}
          onMouseEnter={() => !disabled && setHover(n)}
          onMouseLeave={() => !disabled && setHover(null)} />
      ))}
      {value && <span className="dot-score" style={{ color: accent }}>{value}<span style={{ color: "#333", fontSize: "10px" }}>/10</span></span>}
    </div>
  );
}

export default function App() {
  const festivalDay = getCurrentFestivalDay();
  const [tab, setTab] = useState("vote");
  const [name, setName] = useState("");
  const [nameConfirmed, setNameConfirmed] = useState(false);
  const [submissions, setSubmissions] = useState([]);
  const [loading, setLoading] = useState(true);
  const [expandedFilm, setExpandedFilm] = useState(null);
  const [dayState, setDayState] = useState({
    1: { ratings: {}, reviews: {} },
    2: { ratings: {}, reviews: {} },
    3: { ratings: {}, reviews: {} },
  });
  // Which days have been submitted this session or reconstructed from storage
  const [submittedDays, setSubmittedDays] = useState({});
  const [justSubmitted, setJustSubmitted] = useState(null); // day number for confirmation flash
  const [saving, setSaving] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => { loadData(); }, []);

  // When name is confirmed, hydrate dayState from storage and reconstruct submitted days
  useEffect(() => {
    if (!nameConfirmed) return;
    const entry = submissions.find(s => s.name.toLowerCase() === name.toLowerCase());
    if (!entry) return;
    // Populate dayState from stored data so there is one source of truth
    setDayState(prev => {
      const next = { ...prev };
      [1, 2, 3].forEach(day => {
        const dr = entry.dayRatings?.[day];
        if (dr) {
          next[day] = {
            ratings: dr.ratings || {},
            reviews: dr.reviews || {},
          };
        }
      });
      return next;
    });
    setSubmittedDays(getSubmittedDays(submissions, name));
  }, [nameConfirmed, submissions, name]);

  async function loadData() {
    setLoading(true);
    try {
      const r = await window.storage.get(STORAGE_KEY, true);
      if (r?.value) setSubmissions(JSON.parse(r.value));
    } catch (e) {}
    setLoading(false);
  }

  function setRating(day, id, v) {
    setDayState(p => ({ ...p, [day]: { ...p[day], ratings: { ...p[day].ratings, [id]: v } } }));
  }
  function setReview(day, id, v) {
    setDayState(p => ({ ...p, [day]: { ...p[day], reviews: { ...p[day].reviews, [id]: v } } }));
  }
  function dayRated(day) {
    return FILMS.filter(f => f.day === day).every(f => dayState[day].ratings[f.id] != null);
  }

  async function submitDay(day) {
    const n = name.trim();
    if (!n || !dayRated(day)) return;
    setSaving(day); setError(null);

    // Clean reviews: trim whitespace, drop blanks
    const cleanReviews = {};
    Object.entries(dayState[day].reviews).forEach(([k, v]) => {
      const trimmed = (v || "").trim();
      if (trimmed) cleanReviews[k] = trimmed;
    });

    const dayData = { ratings: dayState[day].ratings, reviews: cleanReviews };
    const existing = submissions.find(s => s.name.toLowerCase() === n.toLowerCase());
    let newSubs;
    if (existing) {
      newSubs = submissions.map(s => s.name.toLowerCase() !== n.toLowerCase() ? s
        : { ...s, dayRatings: { ...s.dayRatings, [day]: dayData } });
    } else {
      newSubs = [...submissions, { name: n, dayRatings: { [day]: dayData }, timestamp: Date.now() }];
    }
    await window.storage.set(STORAGE_KEY, JSON.stringify(newSubs), true);
    setSubmissions(newSubs);
    setSubmittedDays(prev => ({ ...prev, [day]: true }));
    setJustSubmitted(day);
    setTimeout(() => setJustSubmitted(null), 4000);
    setSaving(null);
  }

  const ranked = [...FILMS].map(film => {
    const { avg, count } = getAvg(submissions, film);
    return { ...film, avg, count };
  }).filter(f => f.avg !== null).sort((a, b) => b.avg - a.avg);

  return (
    <>
      <style>{css}</style>
      <div className="grain" />
      <div className="scratch scratch-1" />
      <div className="scratch scratch-2" />
      <div className="app">

        <div className="hero">
          <div className="eyebrow">Deutsche Schule Prag · Project Week 2026</div>
          <div className="festival-title">POPCORN<br /><span className="cinema">CINEMA</span></div>
          <div className="byline">Filme, die unterhalten, provozieren und Fragen stellen, die zählen.</div>
        </div>

        <nav className="nav">
          {[["vote","Rate"],["films","Films"],["leaderboard","Ranking"]].map(([t, label]) => (
            <button key={t} className={`nav-btn${tab === t ? " active" : ""}`} onClick={() => setTab(t)}>{label}</button>
          ))}
        </nav>

        <div className="content">
          {loading && <div className="empty">Loading…</div>}

          {/* VOTE */}
          {!loading && tab === "vote" && (
            <>
              {festivalDay === 0 && <div className="locked-screen">The festival opens on 22 June.</div>}

              {festivalDay > 0 && !nameConfirmed && (
                <div className="name-screen">
                  <p className="intro-text">Rate the films after each day. Both films must be scored to submit — reviews are optional.</p>
                  <p className="name-hint">If another student shares your name, add your surname initial.</p>
                  <label className="name-label">Your name</label>
                  <div className="name-row">
                    <input className="name-input" value={name} onChange={e => setName(e.target.value)}
                      onKeyDown={e => e.key === "Enter" && name.trim() && setNameConfirmed(true)}
                      placeholder="First name + initial" />
                    <button className="name-btn" onClick={() => name.trim() && setNameConfirmed(true)}>Continue</button>
                  </div>
                </div>
              )}

              {festivalDay > 0 && nameConfirmed && (
                <>
                  <div className="voting-as">
                    Voting as <strong>{name}</strong>
                    <button onClick={() => { setNameConfirmed(false); setSubmittedDays({}); setDayState({ 1: { ratings: {}, reviews: {} }, 2: { ratings: {}, reviews: {} }, 3: { ratings: {}, reviews: {} } }); }}>change</button>
                  </div>

                  {[1,2,3].map(day => {
                    const unlocked = day <= festivalDay;
                    const ds = dayState[day];
                    const isSubmitted = !!submittedDays[day];
                    const films = FILMS.filter(f => f.day === day);
                    const rated = dayRated(day);

                    return (
                      <div key={day} className="day-block">
                        <div className="day-label">
                          Day {day} · {DAY_DATES[day]}
                          {!unlocked && <span className="locked-badge">Unlocks {DAY_DATES[day]}</span>}
                          {unlocked && isSubmitted && <span className="submitted-badge">✓ Submitted</span>}
                        </div>

                        {films.map(film => {
                          const displayRating = ds.ratings[film.id];
                          const displayReview = ds.reviews[film.id];
                          const { avg, count } = getAvg(submissions, film);

                          return (
                            <div key={film.id} className={`film-card${!unlocked ? " locked" : ""}`}>
                              <div className="film-card-accent" style={{ background: film.accent }} />
                              <div className="film-card-inner">
                                <div className="film-title">{film.title}</div>
                                <div className="film-meta">dir. {film.director} · {film.year}</div>
                                <FilmDots value={displayRating}
                                  onChange={unlocked && !isSubmitted ? v => setRating(day, film.id, v) : null}
                                  disabled={!unlocked || isSubmitted} accent={film.accent} />
                                {/* Show class average once submitted */}
                                {isSubmitted && avg !== null && (
                                  <div className="film-avg-inline">
                                    Class average: <span style={{ color: film.accent }}>{avg.toFixed(1)}/10</span>
                                    <span style={{ color: "#1e1e1e" }}> · {count} vote{count !== 1 ? "s" : ""}</span>
                                  </div>
                                )}
                                {unlocked && !isSubmitted && (
                                  <textarea className="review-input" rows={2}
                                    placeholder="Say something about it…"
                                    value={ds.reviews[film.id] || ""}
                                    onChange={e => setReview(day, film.id, e.target.value)} />
                                )}
                                {isSubmitted && displayReview && (
                                  <div className="submitted-review">"{displayReview}"</div>
                                )}
                              </div>
                            </div>
                          );
                        })}

                        {unlocked && !isSubmitted && (
                          <div style={{ marginTop: "12px" }}>
                            {error && <div className="error-msg">{error}</div>}
                            <button className={`submit-btn${rated ? " ready" : ""}`}
                              onClick={() => rated && submitDay(day)}
                              disabled={saving === day}>
                              {saving === day ? "Submitting…" : rated ? `Submit Day ${day} →` : "Rate both films to continue"}
                            </button>
                          </div>
                        )}

                        {justSubmitted === day && (
                          <div className="confirm-banner">
                            <div className="confirm-banner-title">Day {day} recorded.</div>
                            <div className="confirm-banner-sub">Your ratings have been saved. {day < 3 ? `Come back tomorrow for Day ${day + 1}.` : `Thanks for taking part in Popcorn Cinema.`}</div>
                          </div>
                        )}
                      </div>
                    );
                  })}
                </>
              )}
            </>
          )}

          {/* FILMS */}
          {!loading && tab === "films" && (
            <>
              <div style={{ fontFamily: "'DM Mono', monospace", fontSize: "10px", letterSpacing: "0.2em", color: "#222", textTransform: "uppercase", marginBottom: "28px" }}>
                {submissions.length} submission{submissions.length !== 1 ? "s" : ""}
              </div>
              {[1,2,3].map(day => (
                <div key={day} className="day-block">
                  <div className="day-label">Day {day} · {DAY_DATES[day]}</div>
                  {FILMS.filter(f => f.day === day).map(film => {
                    const { avg, count } = getAvg(submissions, film);
                    const reviews = submissions.filter(s => s.dayRatings?.[film.day]?.reviews?.[film.id]);
                    const isOpen = expandedFilm === film.id;
                    return (
                      <div key={film.id}>
                        <div className="film-row" onClick={() => setExpandedFilm(isOpen ? null : film.id)}>
                          <div style={{ flex: 1 }}>
                            <div className="film-row-title" style={{ borderLeft: `2px solid ${film.accent}`, paddingLeft: "12px" }}>{film.title}</div>
                            <div className="film-row-meta" style={{ paddingLeft: "14px" }}>dir. {film.director} · {reviews.length} review{reviews.length !== 1 ? "s" : ""}</div>
                          </div>
                          {avg !== null
                            ? <div><div className="big-score" style={{ color: film.accent }}>{avg.toFixed(1)}</div><div className="big-score-sub">{count} vote{count !== 1 ? "s" : ""}</div></div>
                            : <div className="big-score" style={{ color: "#1a1a1a" }}>—</div>}
                        </div>
                        {isOpen && (
                          <div className="reviews-panel">
                            {reviews.length === 0
                              ? <div className="no-reviews">No written reviews yet.</div>
                              : reviews.map((s, i) => (
                                <div key={i} className="review-item">
                                  <div className="review-author">
                                    <span style={{ color: film.accent }}>{s.name}</span>
                                    <span className="review-score">{s.dayRatings[film.day].ratings[film.id]}/10</span>
                                  </div>
                                  <div className="review-text">{s.dayRatings[film.day].reviews[film.id]}</div>
                                </div>
                              ))}
                          </div>
                        )}
                      </div>
                    );
                  })}
                </div>
              ))}
            </>
          )}

          {/* LEADERBOARD */}
          {!loading && tab === "leaderboard" && (
            <>
              {ranked.length === 0
                ? <div className="empty">No votes in yet.</div>
                : ranked.map((film, i) => (
                  <div key={film.id} className="lb-row">
                    <div className={`lb-rank${i === 0 ? " gold" : ""}`}>{i + 1}</div>
                    <div style={{ flex: 1 }}>
                      <div className="lb-title">{film.title}</div>
                      <div className="lb-day">Day {film.day} · {film.count} vote{film.count !== 1 ? "s" : ""}</div>
                    </div>
                    <div className="lb-score" style={{ color: film.accent }}>{film.avg.toFixed(1)}</div>
                  </div>
                ))
              }
              {submissions.length > 0 && (
                <div className="voters-section">
                  <div className="voters-label">Voters</div>
                  {submissions.map((s, i) => <span key={i} className="voter-chip">{s.name}</span>)}
                </div>
              )}
            </>
          )}
        </div>
      </div>
    </>
  );
}
