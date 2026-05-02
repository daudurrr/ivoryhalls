<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ivory Halls — A Confidential Prospectus</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400;1,600&family=Cinzel+Decorative:wght@400;700&family=IM+Fell+English:ital@0;1&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #1a1410;
    --parchment: #f5ede0;
    --parchment-dark: #ede0cb;
    --gold: #b8922a;
    --gold-light: #d4ac4a;
    --gold-pale: #e8d49a;
    --crimson: #6b1a1a;
    --crimson-deep: #3d0d0d;
    --ivory: #faf6ee;
    --ash: #2e2820;
    --mist: #c5b89a;
    --shadow: rgba(10,6,2,0.6);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  @page {
    size: A4;
    margin: 0;
  }

  body {
    background: #0d0a07;
    font-family: 'Cormorant Garamond', 'Georgia', serif;
    color: var(--ink);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem 1rem 4rem;
  }

  .document {
    width: 100%;
    max-width: 780px;
    background: var(--parchment);
    position: relative;
    box-shadow:
      0 0 0 1px #6b4a1a,
      0 0 0 4px #2a1a0a,
      0 0 0 5px #6b4a1a,
      0 0 60px rgba(0,0,0,0.9),
      inset 0 0 120px rgba(160,100,30,0.08);
  }

  /* Decorative corner ornaments via CSS */
  .document::before, .document::after {
    content: '';
    position: absolute;
    width: 60px;
    height: 60px;
    border-color: var(--gold);
    border-style: solid;
    opacity: 0.6;
    z-index: 10;
  }
  .document::before {
    top: 14px; left: 14px;
    border-width: 2px 0 0 2px;
  }
  .document::after {
    bottom: 14px; right: 14px;
    border-width: 0 2px 2px 0;
  }

  .corner-br, .corner-tl-inner {
    position: absolute;
    width: 60px;
    height: 60px;
    border-color: var(--gold);
    border-style: solid;
    opacity: 0.6;
    z-index: 10;
    pointer-events: none;
  }
  .corner-br { bottom: 14px; left: 14px; border-width: 0 0 2px 2px; }
  .corner-tr { top: 14px; right: 14px; border-width: 2px 2px 0 0; position: absolute; width: 60px; height: 60px; border-color: var(--gold); border-style: solid; opacity: 0.6; z-index: 10; pointer-events: none; }

  /* Worn parchment texture simulation */
  .parchment-texture {
    position: absolute;
    inset: 0;
    background-image:
      radial-gradient(ellipse at 20% 10%, rgba(120,80,20,0.06) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 90%, rgba(100,60,10,0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 60% 40%, rgba(0,0,0,0.03) 0%, transparent 40%);
    pointer-events: none;
    z-index: 1;
  }

  .inner-content {
    position: relative;
    z-index: 2;
    padding: 60px 72px;
  }

  /* ---- COVER ---- */
  .cover {
    text-align: center;
    padding: 80px 72px 60px;
    background: linear-gradient(180deg, #1a0f06 0%, #0d0a07 40%, #0d0a07 60%, #1a0f06 100%);
    position: relative;
    overflow: hidden;
  }

  .cover::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      radial-gradient(ellipse at 50% 30%, rgba(184,146,42,0.12) 0%, transparent 60%),
      radial-gradient(ellipse at 50% 80%, rgba(107,26,26,0.15) 0%, transparent 50%);
  }

  .cover-inner {
    position: relative;
    z-index: 2;
  }

  .cover-eyebrow {
    font-family: 'Cinzel Decorative', serif;
    font-size: 8.5px;
    letter-spacing: 0.45em;
    color: var(--mist);
    text-transform: uppercase;
    margin-bottom: 2rem;
    opacity: 0.7;
  }

  .cover-title {
    font-family: 'Cinzel Decorative', serif;
    font-size: 56px;
    font-weight: 700;
    color: var(--gold-pale);
    letter-spacing: 0.12em;
    line-height: 1.1;
    text-shadow:
      0 0 60px rgba(184,146,42,0.4),
      0 2px 4px rgba(0,0,0,0.8);
    margin-bottom: 0.3rem;
  }

  .cover-subtitle {
    font-family: 'IM Fell English', serif;
    font-style: italic;
    font-size: 16px;
    color: var(--mist);
    letter-spacing: 0.08em;
    margin-bottom: 2.5rem;
    opacity: 0.8;
  }

  .cover-divider {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin: 1.5rem auto;
    max-width: 340px;
  }

  .divider-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
  }

  .divider-ornament {
    color: var(--gold);
    font-size: 18px;
    opacity: 0.8;
  }

  .cover-seal {
    margin: 2rem auto 0;
    width: 80px;
    height: 80px;
    border: 1.5px solid var(--gold);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    opacity: 0.7;
  }

  .cover-seal::before {
    content: '';
    position: absolute;
    inset: 5px;
    border: 0.5px solid var(--gold);
    border-radius: 50%;
    opacity: 0.5;
  }

  .seal-text {
    font-family: 'Cinzel Decorative', serif;
    font-size: 22px;
    color: var(--gold-pale);
  }

  .cover-tagline {
    font-family: 'IM Fell English', serif;
    font-style: italic;
    font-size: 13px;
    color: var(--mist);
    letter-spacing: 0.12em;
    margin-top: 1.5rem;
    opacity: 0.5;
  }

  /* ---- BODY ---- */
  .body-section {
    padding: 56px 72px;
    border-top: 1px solid rgba(120,80,20,0.2);
  }

  .section-header {
    text-align: center;
    margin-bottom: 2.5rem;
  }

  .section-number {
    font-family: 'Cinzel Decorative', serif;
    font-size: 9px;
    letter-spacing: 0.5em;
    color: var(--gold);
    text-transform: uppercase;
    opacity: 0.7;
    display: block;
    margin-bottom: 0.5rem;
  }

  .section-title {
    font-family: 'Cinzel Decorative', serif;
    font-size: 20px;
    font-weight: 400;
    color: var(--ash);
    letter-spacing: 0.15em;
  }

  .section-title.crimson {
    color: var(--crimson);
  }

  .ornament-divider {
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 1.2rem 0 2rem;
    justify-content: center;
  }

  .ornament-divider .line {
    height: 1px;
    width: 80px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
  }

  .ornament-divider .dot {
    width: 4px;
    height: 4px;
    background: var(--gold);
    border-radius: 50%;
    opacity: 0.7;
  }

  .ornament-divider .diamond {
    width: 6px;
    height: 6px;
    background: var(--gold);
    transform: rotate(45deg);
    opacity: 0.8;
  }

  p {
    font-family: 'IM Fell English', serif;
    font-size: 15.5px;
    line-height: 1.85;
    color: #2a2018;
    text-align: justify;
    margin-bottom: 1.2em;
    hyphens: auto;
  }

  p:last-child { margin-bottom: 0; }

  .drop-cap::first-letter {
    font-family: 'Cinzel Decorative', serif;
    font-size: 4.2em;
    font-weight: 700;
    float: left;
    line-height: 0.75;
    margin-right: 0.08em;
    margin-top: 0.05em;
    color: var(--crimson);
  }

  .pull-quote {
    margin: 2rem 0;
    padding: 1.4rem 2rem;
    border-left: 2.5px solid var(--gold);
    border-right: 2.5px solid var(--gold);
    background: rgba(184,146,42,0.04);
    text-align: center;
  }

  .pull-quote p {
    font-style: italic;
    font-size: 17px;
    color: var(--crimson);
    text-align: center;
    margin: 0;
    letter-spacing: 0.02em;
  }

  /* Rules table */
  .rules-list {
    list-style: none;
    padding: 0;
    margin: 1.5rem 0;
  }

  .rules-list li {
    font-family: 'IM Fell English', serif;
    font-size: 15px;
    line-height: 1.7;
    color: #2a2018;
    padding: 0.6rem 0;
    border-bottom: 1px solid rgba(120,80,20,0.12);
    display: flex;
    gap: 1rem;
    align-items: baseline;
  }

  .rules-list li:last-child {
    border-bottom: none;
  }

  .rule-num {
    font-family: 'Cinzel Decorative', serif;
    font-size: 10px;
    color: var(--gold);
    opacity: 0.9;
    letter-spacing: 0.1em;
    min-width: 22px;
    padding-top: 3px;
  }

  /* Two-column layout for some sections */
  .two-col {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2.5rem;
  }

  .col-heading {
    font-family: 'Cinzel Decorative', serif;
    font-size: 11px;
    letter-spacing: 0.3em;
    color: var(--crimson);
    text-transform: uppercase;
    margin-bottom: 0.9rem;
    display: block;
  }

  /* Tier cards */
  .tier-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    margin: 1.5rem 0;
  }

  .tier-card {
    border: 1px solid rgba(120,80,20,0.3);
    padding: 1.4rem 1.2rem;
    background: rgba(250,246,238,0.6);
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .tier-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: var(--gold);
    opacity: 0.4;
  }

  .tier-card.featured::before {
    background: linear-gradient(90deg, var(--crimson), var(--gold), var(--crimson));
    opacity: 0.9;
    height: 3px;
  }

  .tier-name {
    font-family: 'Cinzel Decorative', serif;
    font-size: 10px;
    letter-spacing: 0.35em;
    color: var(--gold);
    text-transform: uppercase;
    display: block;
    margin-bottom: 0.5rem;
  }

  .tier-title {
    font-family: 'IM Fell English', serif;
    font-style: italic;
    font-size: 19px;
    color: var(--crimson);
    display: block;
    margin-bottom: 0.8rem;
  }

  .tier-desc {
    font-family: 'Cormorant Garamond', serif;
    font-size: 13px;
    line-height: 1.6;
    color: #4a3828;
    text-align: center;
  }

  /* Footer */
  .footer {
    background: #0d0a07;
    padding: 2rem 72px;
    text-align: center;
  }

  .footer-text {
    font-family: 'Cinzel Decorative', serif;
    font-size: 9px;
    letter-spacing: 0.5em;
    color: var(--mist);
    text-transform: uppercase;
    opacity: 0.4;
    font-style: normal;
  }

  .footer-text p {
    font-family: 'Cinzel Decorative', serif;
    font-size: 9px;
    letter-spacing: 0.5em;
    color: var(--mist);
    opacity: 0.4;
    text-align: center;
  }

  /* Horizontal rule variant */
  .hr-ornate {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    margin: 2rem 0;
    opacity: 0.5;
  }

  .hr-ornate::before, .hr-ornate::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--gold);
  }

  .hr-ornate span {
    color: var(--gold);
    font-size: 14px;
    letter-spacing: 4px;
  }

  /* Warning block */
  .notice-box {
    border: 1px solid var(--crimson);
    padding: 1.2rem 1.6rem;
    margin: 2rem 0;
    background: rgba(107,26,26,0.04);
    position: relative;
  }

  .notice-box::before {
    content: '✦';
    position: absolute;
    top: -9px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--parchment);
    padding: 0 8px;
    color: var(--crimson);
    font-size: 12px;
  }

  .notice-box p {
    font-style: italic;
    font-size: 14px;
    color: var(--crimson-deep);
    text-align: center;
    margin: 0;
  }

  em {
    color: var(--crimson);
  }

  @media print {
    body {
      background: white;
      padding: 0;
    }
    .document {
      box-shadow: none;
      max-width: 100%;
    }
    .cover {
      background: #0d0a07 !important;
      -webkit-print-color-adjust: exact;
      print-color-adjust: exact;
    }
    .footer {
      background: #0d0a07 !important;
      -webkit-print-color-adjust: exact;
      print-color-adjust: exact;
    }
  }
</style>
</head>
<body>

<div class="document">
  <div class="parchment-texture"></div>
  <div class="corner-br"></div>
  <div class="corner-tr"></div>

  <!-- COVER -->
  <div class="cover">
    <div class="cover-inner">
      <div class="cover-eyebrow">A Confidential Prospectus &nbsp;·&nbsp; For Invited Guests Only</div>

      <div class="cover-divider">
        <div class="divider-line"></div>
        <div class="divider-ornament">✦</div>
        <div class="divider-line"></div>
      </div>

      <h1 class="cover-title">Ivory<br>Halls</h1>
      <div class="cover-subtitle">Where Every Want Is Already Known</div>

      <div class="cover-divider">
        <div class="divider-line"></div>
        <div class="divider-ornament">✦</div>
        <div class="divider-ornament">◆</div>
        <div class="divider-ornament">✦</div>
        <div class="divider-line"></div>
      </div>

      <div class="cover-seal">
        <span class="seal-text">IH</span>
      </div>

      <div class="cover-tagline">Est. Before Memory &nbsp;·&nbsp; Open Until You Are Done</div>
    </div>
  </div>

  <!-- SECTION I: NATURE -->
  <div class="body-section">
    <div class="inner-content" style="padding-left:0; padding-right:0;">
      <div class="section-header">
        <span class="section-number">— I —</span>
        <h2 class="section-title">On the Nature of the Establishment</h2>
        <div class="ornament-divider">
          <div class="line"></div>
          <div class="dot"></div>
          <div class="diamond"></div>
          <div class="dot"></div>
          <div class="line"></div>
        </div>
      </div>

      <p class="drop-cap">The Ivory Halls are not found so much as <em>encountered</em>. One may hear of them through a whisper at the right sort of party, or through the recommendation of a friend who has since stopped speaking of certain evenings altogether. There is no address. There is no fixed district. Every patron who has sought the door a second time found it in a different wall, in a different street — and yet the threshold is always unmistakable. Those who have crossed it once describe, when pressed, something less like memory and more like <em>pull</em>: a knowledge in the body rather than the mind, drawing them back as reliably and as helplessly as a flame draws what it means to consume.</p>

      <p>Whatever form the entrance takes on a given evening, what lies beyond it does not change. The geometry inside is complicated in ways that resist description. Hallways extend farther than any building could permit. Rooms open onto other rooms with no corridor between. Staircases spiral in directions that cannot be reconciled with any map. Guests are advised not to attempt the mapping.</p>

      <div class="pull-quote">
        <p>"The Ivory Halls do not tempt. They <em>recognise</em>.<br>What you find here was always already yours."</p>
      </div>

      <p>This is a place of pleasures, broadly construed. The Halls cater to appetites both ordinary and rarefied — to those who seek entertainment, company, intoxication, information, forgetting. What precisely is offered in the deeper rooms is not disclosed in writing, for the simple reason that what is offered changes to suit whoever is asking. The Halls do not merely accommodate desire; they <em>cultivate</em> it — with patience, with attentiveness, with an investment in the guest's appetite that borders on the devotional. What you consume here, the Halls consume in kind. This arrangement suits everyone very well.</p>
    </div>
  </div>

  <!-- SECTION II: SOCIETY -->
  <div class="body-section">
    <div class="inner-content" style="padding-left:0; padding-right:0;">
      <div class="section-header">
        <span class="section-number">— II —</span>
        <h2 class="section-title crimson">The Society of Patrons</h2>
        <div class="ornament-divider">
          <div class="line"></div>
          <div class="dot"></div>
          <div class="diamond"></div>
          <div class="dot"></div>
          <div class="line"></div>
        </div>
      </div>

      <p>One does not apply for membership at the Ivory Halls. One is <em>considered</em>. The process by which consideration occurs is opaque by design; it involves parties unknown, criteria unstated, and a timeline entirely indifferent to urgency. Those who push for an invitation tend not to receive one.</p>

      <p>The patrons of the Halls are, as a matter of observed fact, persons of consequence: merchants of sufficient standing, minor nobles with interesting vices, scholars whose research has grown inconveniently specific, officials whose discretion can be purchased, and a small but notable contingent of individuals whose names do not appear in any public record and whose occupations defy straightforward description. They share, by and large, the quality of wanting something they cannot obtain elsewhere.</p>

      <div class="tier-grid">
        <div class="tier-card">
          <span class="tier-name">First Tier</span>
          <span class="tier-title">The Welcomed</span>
          <p class="tier-desc">Invited guests, new to the Halls. Access to the parlours, the common pleasures, and the first three floors. Their wants are attended to. Their secrets are noted.</p>
        </div>
        <div class="tier-card featured">
          <span class="tier-name">Second Tier</span>
          <span class="tier-title">The Familiar</span>
          <p class="tier-desc">Patrons who have returned, and returned again. The Halls have learned their appetites. Access is broader. The price, accordingly, is higher — though it is rarely denominated in coin.</p>
        </div>
        <div class="tier-card">
          <span class="tier-name">Third Tier</span>
          <span class="tier-title">The Indebted</span>
          <p class="tier-desc">Those who have consumed beyond their means, in one currency or another. They do not leave. Not yet. They are given, instead, purpose — which is to say, they are given work.</p>
        </div>
      </div>

      <div class="notice-box">
        <p>No patron of the Ivory Halls may speak of the Halls to persons uninvited. This is not a rule enforced by punishment. It is a rule enforced by the Halls themselves, in ways guests have thus far found it unpleasant to describe.</p>
      </div>
    </div>
  </div>

  <!-- SECTION III: STAFF -->
  <div class="body-section">
    <div class="inner-content" style="padding-left:0; padding-right:0;">
      <div class="section-header">
        <span class="section-number">— III —</span>
        <h2 class="section-title">Staff &amp; Overwatch</h2>
        <div class="ornament-divider">
          <div class="line"></div>
          <div class="dot"></div>
          <div class="diamond"></div>
          <div class="dot"></div>
          <div class="line"></div>
        </div>
      </div>

      <div class="two-col">
        <div>
          <span class="col-heading">The Attendants</span>
          <p style="font-size:14.5px; text-align:left;">The staff of the Ivory Halls are possessed of a quality difficult to name — something between attentiveness and <em>foreknowledge</em>. They move softly. They smile at precisely the right moment. They will bring what you require before you have asked for it, and they will do so with a graciousness so exact it passes, on a good evening, for warmth. They will not answer questions about themselves, about the building, or about the other guests, and they will not be offended when you try.</p>
          <p style="font-size:14.5px; text-align:left;">Look at one directly for too long and something shifts — not in their expression, which remains perfectly composed, but in the quality of the air around them, in the faint sense that whatever you are looking at has arranged itself, for your benefit, into the approximate shape of a person.</p>
        </div>
        <div>
          <span class="col-heading">The Proprietor</span>
          <p style="font-size:14.5px; text-align:left;">Above the Attendants stands something else. The Halls are held, in the loosest possible sense of the word, by an interest referred to — when referred to at all — as <em>the Proprietor</em>. This figure does not circulate among guests in any ordinary way. Evidence of their attention manifests in other fashions: in a door that was not there yesterday, in the way a certain corridor smells of somewhere else entirely, in a patron who checked out without checking in. Guests who ask about the Proprietor directly are redirected, graciously, to the matter of their drinks.</p>
          <p style="font-size:14.5px; text-align:left;">A personal audience with the Proprietor can, under rare circumstances, be arranged — though the channel for such a request is itself not obvious, and the meeting, once granted, is not always what was anticipated. Those who have emerged from one tend to choose their words carefully thereafter.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- SECTION IV: RULES -->
  <div class="body-section">
    <div class="inner-content" style="padding-left:0; padding-right:0;">
      <div class="section-header">
        <span class="section-number">— IV —</span>
        <h2 class="section-title crimson">The Compact of the House</h2>
        <div class="ornament-divider">
          <div class="line"></div>
          <div class="dot"></div>
          <div class="diamond"></div>
          <div class="dot"></div>
          <div class="line"></div>
        </div>
      </div>

      <p>Every invited guest, upon first crossing the threshold, implicitly accepts the terms of the House Compact. These are not secret, merely seldom volunteered. They are reproduced below as a courtesy to new patrons, and as a reminder to those who have let certain provisions slip from mind.</p>

      <ul class="rules-list">
        <li><span class="rule-num">I.</span> A guest does not ask after another guest. What happens in the Halls belongs to the Halls.</li>
        <li><span class="rule-num">II.</span> Certain appetites — including those of a violent disposition — have their place within the Halls, and rooms exist for precisely that purpose. Outside of these designated arrangements, harm visited upon staff, fellow patrons, or the fabric of the building carries consequence. The Halls do not punish impulsively. They account, with great patience, and they collect in their own time.</li>
        <li><span class="rule-num">III.</span> Nothing passes out of the Halls without the Halls permitting it — whether object, person, or confidence exchanged between parties. Guests who wish to extend an invitation to an outside party, or to arrange for some specific permission of departure, must seek a personal audience with the Proprietor. Such arrangements are possible. They are not simple, and they are not free.</li>
        <li><span class="rule-num">IV.</span> A guest does not attempt to locate, map, or document any portion of the building beyond the public floors. The private levels are private. The deepest levels are not, in the strictest sense, navigable by the unaccompanied.</li>
        <li><span class="rule-num">V.</span> All debts accrued within the Halls — of coin, of favour, of confidence — are acknowledged. Acknowledgement constitutes obligation. Obligation accrues interest of a kind that varies by debtor.</li>
        <li><span class="rule-num">VI.</span> The Halls may, at any time and without explanation, decline to show the exit to a particular guest. What follows is between that guest and the Halls, and does not proceed according to any logic that has been successfully documented. Those who have returned from such an interval are reluctant, as a rule, to discuss the specifics. What can be said is that they return changed — and that changed, in this context, is a word capacious enough to cover a very great deal.</li>
      </ul>

      <div class="hr-ornate"><span>✦ ◆ ✦</span></div>

      <p style="text-align:center; font-style:italic; font-size:14px; color: #5a4030;">The management thanks you for your patronage and trusts that your visit will be everything you hoped for.<br>And perhaps rather more.</p>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="cover-divider" style="max-width:200px; margin: 0 auto 1rem;">
      <div class="divider-line"></div>
      <div class="divider-ornament" style="font-size:12px;">✦</div>
      <div class="divider-line"></div>
    </div>
    <div class="footer-text">
      <p>Ivory Halls &nbsp;·&nbsp; No Fixed Address &nbsp;·&nbsp; By Invitation Only</p>
      <p style="margin-top: 0.5rem; font-size: 8px; letter-spacing: 0.3em;">This document is the property of the Ivory Halls and returns to them in time.</p>
    </div>
  </div>

</div>
</body>
</html>
