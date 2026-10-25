<!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#0B2545">
<title>Business Content Maker</title>
<style>
  :root {
    --navy: #0B2545;
    --navy-soft: #13315C;
    --teal: #0B7F85;
    --teal-dark: #086267;
    --teal-light: #E3F4F4;
    --white: #FFFFFF;
    --bg: #F4F7FA;
    --text: #12263F;
    --muted: #4A5B70;
    --border: #C9D4E0;
    --error: #B3261E;index.html
    --warn-bg: #FFF7E0;
    --warn-border: #E0B63C;
    --radius: 14px;
  }
  * { box-sizing: border-box; }
  html { -webkit-text-size-adjust: 100%; }
  body {
    margin: 0;
    font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 18px;
    line-height: 1.55;
    color: var(--text);
    background: var(--bg);
  }
  header {
    background: var(--navy);
    color: var(--white);
    padding: 28px 18px 30px;
    text-align: center;
    border-bottom: 5px solid var(--teal);
  }
  header h1 { margin: 0 0 6px; font-size: 1.7rem; line-height: 1.2; }
  header p { margin: 0 auto; max-width: 34rem; color: #D6E2F0; font-size: 1.02rem; }
  main { max-width: 680px; margin: 0 auto; padding: 18px 16px 40px; }
  .card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px 18px;
    margin-bottom: 18px;
    box-shadow: 0 2px 8px rgba(11, 37, 69, 0.07);
  }
  .notice {
    background: var(--warn-bg);
    border: 2px solid var(--warn-border);
    border-radius: var(--radius);
    padding: 14px 16px;
    margin-bottom: 18px;
    font-size: 1rem;
  }
  .notice strong { color: var(--navy); }
  h2 { margin: 0 0 14px; font-size: 1.3rem; color: var(--navy); }
  .field { margin-bottom: 20px; }
  label, legend {
    display: block;
    font-weight: 700;
    color: var(--navy);
    margin-bottom: 6px;
    padding: 0;
  }
  .hint { display: block; font-weight: 400; font-size: 0.92rem; color: var(--muted); margin-top: 2px; }
  input[type="text"] {
    width: 100%;
    min-height: 54px;
    padding: 12px 14px;
    font: inherit;
    color: var(--text);
    background: var(--white);
    border: 2px solid var(--border);
    border-radius: 10px;
  }
  input[type="text"]:focus { outline: 3px solid var(--teal); outline-offset: 1px; border-color: var(--teal); }
  input[aria-invalid="true"] { border-color: var(--error); }
  .error-msg { color: var(--error); font-size: 0.95rem; font-weight: 600; margin: 6px 0 0; min-height: 0; }
  fieldset { border: 0; margin: 0 0 20px; padding: 0; min-width: 0; }
  .seg { display: flex; flex-wrap: wrap; gap: 10px; }
  .seg .opt { position: relative; flex: 1 1 28%; min-width: 96px; }
  .seg input {
    position: absolute; opacity: 0; width: 100%; height: 100%; top: 0; left: 0; margin: 0; cursor: pointer;
  }
  .seg label {
    display: flex; align-items: center; justify-content: center; text-align: center;
    min-height: 54px; margin: 0; padding: 10px 8px;
    border: 2px solid var(--border); border-radius: 10px;
    background: var(--white); color: var(--navy); font-weight: 700; cursor: pointer;
  }
  .seg input:checked + label { background: var(--navy); color: var(--white); border-color: var(--navy); }
  .seg input:focus-visible + label { outline: 3px solid var(--teal); outline-offset: 2px; }
  button {
    font: inherit; font-weight: 700; min-height: 56px; padding: 12px 18px;
    border-radius: 12px; border: 2px solid transparent; cursor: pointer; width: 100%;
  }
  button:focus-visible { outline: 3px solid var(--navy); outline-offset: 3px; }
  .btn-primary { background: var(--teal); color: var(--white); }
  .btn-primary:active { background: var(--teal-dark); }
  .btn-secondary { background: var(--white); color: var(--navy); border-color: var(--navy); }
  .btn-secondary:active { background: var(--teal-light); }
  .btn-row { display: flex; flex-direction: column; gap: 12px; }
  .result-block { margin-bottom: 18px; }
  .result-block h3 {
    margin: 0 0 6px; font-size: 0.95rem; text-transform: uppercase; letter-spacing: 0.06em; color: var(--teal-dark);
  }
  .result-text {
    background: var(--teal-light); border-left: 5px solid var(--teal);
    border-radius: 8px; padding: 12px 14px; white-space: pre-wrap; word-wrap: break-word; overflow-wrap: anywhere; margin: 0;
  }
  .result-text.headline { font-size: 1.3rem; font-weight: 700; color: var(--navy); }
  #status { min-height: 1.6em; margin: 12px 0 0; font-weight: 700; color: var(--teal-dark); text-align: center; }
  #results[hidden] { display: none; }
  #results:focus { outline: none; }
  footer { text-align: center; color: var(--muted); font-size: 0.9rem; padding: 0 16px 28px; max-width: 680px; margin: 0 auto; }
  @media (min-width: 560px) {
    header h1 { font-size: 2.1rem; }
    .btn-row { flex-direction: row; }
    .btn-row button { flex: 1; }
  }
  @media (prefers-reduced-motion: no-preference) {
    button, .seg label { transition: background 0.15s ease, color 0.15s ease; }
  }
</style>
</head>
<body>

<header>
  <h1>Business Content Maker</h1>
  <p>Fill in a few details and get a headline, caption, call to action, and hashtags for your next post.</p>
</header>

<main>
  <div class="notice" role="note">
    <strong>Please read:</strong> This tool uses ready-made templates that run on your phone. It is <strong>not AI</strong> and does not connect to the internet. The text it creates is a starting point. Always read it, edit it, and check that it is accurate for your business before you publish.
  </div>

  <form id="contentForm" class="card" novalidate>
    <h2>Tell us about your business</h2>

    <div class="field">
      <label for="businessType">Business type
        <span class="hint">Example: bakery, hair salon, plumbing service</span>
      </label>
      <input type="text" id="businessType" name="businessType" maxlength="60" autocomplete="off" aria-describedby="err-businessType" required>
      <p class="error-msg" id="err-businessType" role="alert"></p>
    </div>

    <div class="field">
      <label for="product">Product or service
        <span class="hint">What are you promoting in this post?</span>
      </label>
      <input type="text" id="product" name="product" maxlength="80" autocomplete="off" aria-describedby="err-product" required>
      <p class="error-msg" id="err-product" role="alert"></p>
    </div>

    <div class="field">
      <label for="offer">Special offer (optional)
        <span class="hint">Type your own offer exactly as it is. Leave empty if you have none.</span>
      </label>
      <input type="text" id="offer" name="offer" maxlength="100" autocomplete="off">
    </div>

    <div class="field">
      <label for="customer">Target customer
        <span class="hint">Example: busy parents, students, small business owners</span>
      </label>
      <input type="text" id="customer" name="customer" maxlength="60" autocomplete="off" aria-describedby="err-customer" required>
      <p class="error-msg" id="err-customer" role="alert"></p>
    </div>

    <fieldset>
      <legend>Platform</legend>
      <div class="seg">
        <div class="opt"><input type="radio" id="pl-facebook" name="platform" value="Facebook" checked><label for="pl-facebook">Facebook</label></div>
        <div class="opt"><input type="radio" id="pl-instagram" name="platform" value="Instagram"><label for="pl-instagram">Instagram</label></div>
        <div class="opt"><input type="radio" id="pl-tiktok" name="platform" value="TikTok"><label for="pl-tiktok">TikTok</label></div>
      </div>
    </fieldset>

    <fieldset>
      <legend>Tone</legend>
      <div class="seg">
        <div class="opt"><input type="radio" id="tn-professional" name="tone" value="professional"><label for="tn-professional">Professional</label></div>
        <div class="opt"><input type="radio" id="tn-friendly" name="tone" value="friendly" checked><label for="tn-friendly">Friendly</label></div>
        <div class="opt"><input type="radio" id="tn-funny" name="tone" value="funny"><label for="tn-funny">Funny</label></div>
      </div>
    </fieldset>

    <div class="btn-row">
      <button type="submit" class="btn-primary" id="generateBtn">Generate Content</button>
      <button type="button" class="btn-secondary" id="clearBtn">Clear</button>
    </div>
  </form>

  <section id="results" class="card" tabindex="-1" aria-labelledby="resultsTitle" hidden>
    <h2 id="resultsTitle">Your content</h2>

    <div class="result-block">
      <h3>Headline</h3>
      <p class="result-text headline" id="outHeadline"></p>
    </div>
    <div class="result-block">
      <h3>Promotional caption</h3>
      <p class="result-text" id="outCaption"></p>
    </div>
    <div class="result-block">
      <h3>Call to action</h3>
      <p class="result-text" id="outCta"></p>
    </div>
    <div class="result-block">
      <h3>Hashtags</h3>
      <p class="result-text" id="outTags"></p>
    </div>

    <div class="btn-row">
      <button type="button" class="btn-primary" id="copyBtn">Copy All</button>
      <button type="button" class="btn-secondary" id="againBtn">Generate Again</button>
    </div>
    <p id="status" role="status" aria-live="polite"></p>

    <div class="notice" style="margin:14px 0 0;">
      <strong>Check before publishing:</strong> this content is template-based. Make sure the wording, offer, and details are correct and suit your business and the platform's rules.
    </div>
  </section>
</main>

<footer>
  Works offline. No account, no tracking, no ads. Nothing you type leaves your phone.
</footer>

<script>
(function () {
  "use strict";

  /* ---------- TEMPLATE LIBRARY ----------
     Placeholders: {type} {Type} {product} {Product} {customer} {Customer}
                   {offer} {Offer} {action} {Action}
     Capitalised versions start with a capital letter (used at sentence starts). */

  var TEMPLATES = {
    professional: {
      emoji: [],
      headlines: [
        "{Product} for {customer}",
        "Introducing {product} from our {type}",
        "A closer look at {product}",
        "{Product}, with {customer} in mind",
        "Learn more about {product}"
      ],
      headlinesOffer: [
        "{Product}: {offer}",
        "Current offer on {product}: {offer}",
        "Offer available: {offer}",
        "{Product} with a current offer: {offer}"
      ],
      hooks: [
        "We are pleased to offer {product} to {customer}.",
        "Looking for {product}? Our {type} is here to help {customer}.",
        "Introducing {product} from our {type}, with {customer} in mind.",
        "{Customer}, take a closer look at {product}.",
        "At our {type}, we are focused on {product} for {customer}."
      ],
      bodies: [
        "We aim to keep things clear and simple from the first question to the final step.",
        "Get in touch to find out more about how it works and what to expect.",
        "If you have questions, we are happy to answer them.",
        "Take a moment to see whether it suits what you need."
      ],
      offerLines: [
        "Current offer: {offer}.",
        "Available now: {offer}.",
        "Offer details: {offer}."
      ],
      closers: [
        "Thank you for taking the time to read this.",
        "We look forward to hearing from you.",
        "We appreciate your interest in our {type}."
      ],
      ctas: [
        "Interested in {product}? Please {action}.",
        "To learn more, simply {action}.",
        "Ready to get started? {Action} and we will be glad to help.",
        "Questions about {product}? Just {action}."
      ]
    },

    friendly: {
      emoji: ["😊", "✨", "💬", "👋"],
      headlines: [
        "Hello, {customer}! Meet {product}",
        "{Product} is here for you",
        "Something new from our {type}: {product}",
        "Hi {customer}, say hello to {product}",
        "We are sharing {product} with you"
      ],
      headlinesOffer: [
        "Good news for {customer}: {offer}",
        "{Product} and a little something extra: {offer}",
        "Say hi to {product}: {offer}",
        "A little something for {customer}: {offer}"
      ],
      hooks: [
        "Hi {customer}! We have something we think you will like: {product}.",
        "Hello from our {type}! We are excited to share {product} with {customer}.",
        "{Customer}, this one is for you: {product}.",
        "Looking for {product}? Come and see what our {type} has for you.",
        "We love helping {customer}, and {product} is one way we do it."
      ],
      bodies: [
        "Say hello and ask us anything you would like to know.",
        "We would love to help you find what works for you.",
        "Tell us what you need and we will do our best to help."
      ],
      offerLines: [
        "Good news: {offer}!",
        "Here is something special: {offer}.",
        "Right now: {offer}."
      ],
      closers: [
        "Thanks for being part of our community.",
        "We cannot wait to hear from you!",
        "Tag a friend who might like this."
      ],
      ctas: [
        "Want to know more? Just {action}!",
        "Got a question about {product}? {Action} - we would love to chat!",
        "Ready when you are! {Action}.",
        "Come say hello: {action}."
      ]
    },

    funny: {
      emoji: ["😄", "🎉", "👀", "🤭"],
      headlines: [
        "{Product} has entered the chat",
        "Breaking news, {customer}: {product}",
        "Is it {product} o'clock?",
        "Plot twist: {product}",
        "Fancy some {product}?"
      ],
      headlinesOffer: [
        "Big news: {offer}. Yes, really.",
        "{Product}, but make it {offer}",
        "Spoiler alert: {offer}",
        "Breaking news, {customer}: {offer}"
      ],
      hooks: [
        "Breaking news for {customer}: {product} has entered the chat.",
        "Plot twist: {product} from our {type} might be what you were looking for.",
        "Dear {customer}, your to-do list wants {product} added to it.",
        "Warning: looking at {product} may cause sudden curiosity.",
        "{Customer}, we have {product}. That is the whole joke, and also the whole point."
      ],
      bodies: [
        "No tricks, no magic wands, just our {type} doing what we do.",
        "The only drama here is deciding when to get started.",
        "Ask us anything. We are friendlier than your spam folder."
      ],
      offerLines: [
        "Plot twist: {offer}.",
        "Hold onto your hat: {offer}.",
        "Fun fact: {offer}."
      ],
      closers: [
        "That is all. You may now go about your day.",
        "Okay, we are done talking. Your move.",
        "Thank you for reading. Your attention is appreciated, and so is a good meme."
      ],
      ctas: [
        "Do the smart thing and {action}.",
        "Curious? {Action} before the curiosity wins.",
        "Your next move: {action}.",
        "Be brave and {action}."
      ]
    }
  };

  var PLATFORMS = {
    Facebook:  { action: "message us or leave a comment below", tags: ["FacebookBusiness", "SmallBusiness"] },
    Instagram: { action: "send us a DM or check our bio",       tags: ["InstagramBusiness", "SmallBusiness"] },
    TikTok:    { action: "comment below or follow for more",    tags: ["TikTokBusiness", "SmallBusiness"] }
  };

  var GENERIC_TAGS = ["SmallBusiness", "ShopSmall", "BusinessOwner", "MarketingIdeas", "NewPost"];
  var STOPWORDS = ["a", "an", "and", "the", "for", "of", "to", "in", "on", "with", "or", "at", "by", "our", "my", "your"];

  /* ---------- HELPERS ---------- */

  var lastPick = {};
  function pick(list, key) {
    var i = 0;
    if (list.length > 1) {
      do { i = Math.floor(Math.random() * list.length); } while (i === lastPick[key]);
    }
    lastPick[key] = i;
    return list[i];
  }

  function tidy(s) { return s.replace(/\s+/g, " ").trim(); }
  function stripEnd(s) { return s.replace(/[.!?,;:\s]+$/, ""); }
  function cap(s) { return s.charAt(0).toUpperCase() + s.slice(1); }

  function fill(template, data) {
    return template.replace(/\{(\w+)\}/g, function (match, key) {
      return Object.prototype.hasOwnProperty.call(data, key) ? data[key] : match;
    });
  }

  function toTag(text) {
    var words = text.split(/[^\p{L}\p{N}]+/u).filter(function (w) {
      return w && STOPWORDS.indexOf(w.toLowerCase()) === -1;
    }).slice(0, 3);
    if (!words.length) return "";
    var tag = words.map(function (w) { return cap(w.toLowerCase()); }).join("");
    return (tag.length >= 3 && tag.length <= 30) ? tag : "";
  }

  function buildHashtags(d, platform) {
    var candidates = [toTag(d.type), toTag(d.product), toTag(d.customer)]
      .concat(PLATFORMS[platform].tags)
      .concat(GENERIC_TAGS);
    var seen = {};
    var out = [];
    for (var i = 0; i < candidates.length && out.length < 5; i++) {
      var t = candidates[i];
      if (!t) continue;
      var k = t.toLowerCase();
      if (seen[k]) continue;
      seen[k] = true;
      out.push("#" + t);
    }
    return out.join(" ");
  }

  /* ---------- CONTENT BUILDER ---------- */

  function buildContent(input) {
    var tone = input.tone;
    var platform = input.platform;
    var T = TEMPLATES[tone];
    var hasOffer = input.offer !== "";
    var actionText = PLATFORMS[platform].action;

    var data = {
      type: input.type, Type: cap(input.type),
      product: input.product, Product: cap(input.product),
      customer: input.customer, Customer: cap(input.customer),
      offer: input.offer, Offer: cap(input.offer),
      action: actionText, Action: cap(actionText)
    };

    var headline = fill(pick(hasOffer ? T.headlinesOffer : T.headlines, tone + "-h" + hasOffer), data);
    var hook = fill(pick(T.hooks, tone + "-hook"), data);
    var body = fill(pick(T.bodies, tone + "-body"), data);
    var offerLine = hasOffer ? fill(pick(T.offerLines, tone + "-offer"), data) : "";
    var closer = fill(pick(T.closers, tone + "-closer"), data);
    var cta = fill(pick(T.ctas, tone + "-cta"), data);

    var e1 = T.emoji.length ? pick(T.emoji, tone + "-e1") : "";
    var e2 = T.emoji.length ? pick(T.emoji, tone + "-e2") : "";
    var caption;

    if (platform === "Facebook") {
      var parts = [hook + " " + body];
      if (offerLine) parts.push(offerLine);
      parts.push(closer + (e1 ? " " + e1 : ""));
      caption = parts.join("\n\n");
    } else if (platform === "Instagram") {
      var ig = [(e1 ? e1 + " " : "") + hook, body];
      if (offerLine) ig.push((e2 ? e2 + " " : "") + offerLine);
      ig.push(closer);
      caption = ig.join("\n\n");
    } else { /* TikTok: short and punchy */
      var tt = [hook];
      if (offerLine) tt.push(offerLine);
      tt.push(closer + (e1 ? " " + e1 : ""));
      caption = tt.join("\n");
    }

    return {
      headline: headline,
      caption: caption,
      cta: cta,
      tags: buildHashtags(data, platform)
    };
  }

  /* ---------- PAGE LOGIC ---------- */

  var form = document.getElementById("contentForm");
  var results = document.getElementById("results");
  var statusEl = document.getElementById("status");
  var fields = {
    type:     { el: document.getElementById("businessType"), err: document.getElementById("err-businessType"), label: "your business type" },
    product:  { el: document.getElementById("product"),      err: document.getElementById("err-product"),      label: "your product or service" },
    customer: { el: document.getElementById("customer"),     err: document.getElementById("err-customer"),     label: "your target customer" }
  };
  var offerEl = document.getElementById("offer");

  function checked(name) {
    var el = form.querySelector('input[name="' + name + '"]:checked');
    return el ? el.value : "";
  }

  function validate() {
    var firstBad = null;
    Object.keys(fields).forEach(function (k) {
      var f = fields[k];
      var value = tidy(f.el.value);
      if (!value) {
        f.err.textContent = "Please enter " + f.label + ".";
        f.el.setAttribute("aria-invalid", "true");
        if (!firstBad) firstBad = f.el;
      } else {
        f.err.textContent = "";
        f.el.removeAttribute("aria-invalid");
      }
    });
    if (firstBad) { firstBad.focus(); return false; }
    return true;
  }

  function generate(scroll) {
    if (!validate()) return;
    var input = {
      type: tidy(fields.type.el.value),
      product: tidy(fields.product.el.value),
      customer: tidy(fields.customer.el.value),
      offer: stripEnd(tidy(offerEl.value)),
      platform: checked("platform") || "Facebook",
      tone: checked("tone") || "friendly"
    };
    var out = buildContent(input);
    document.getElementById("outHeadline").textContent = out.headline;
    document.getElementById("outCaption").textContent = out.caption;
    document.getElementById("outCta").textContent = out.cta;
    document.getElementById("outTags").textContent = out.tags;
    statusEl.textContent = "";
    results.hidden = false;
    if (scroll) {
      results.scrollIntoView({ behavior: "smooth", block: "start" });
      results.focus({ preventScroll: true });
    }
  }

  function allText() {
    return [
      document.getElementById("outHeadline").textContent,
      document.getElementById("outCaption").textContent,
      "Call to action: " + document.getElementById("outCta").textContent,
      document.getElementById("outTags").textContent
    ].join("\n\n");
  }

  function fallbackCopy(text) {
    var ta = document.createElement("textarea");
    ta.value = text;
    ta.setAttribute("readonly", "");
    ta.style.position = "fixed";
    ta.style.top = "0";
    ta.style.left = "0";
    ta.style.opacity = "0";
    document.body.appendChild(ta);
    ta.focus();
    ta.select();
    ta.setSelectionRange(0, text.length);
    var ok = false;
    try { ok = document.execCommand("copy"); } catch (e) { ok = false; }
    document.body.removeChild(ta);
    return ok;
  }

  function copyAll() {
    var text = allText();
    function done(ok) {
      statusEl.textContent = ok
        ? "Copied! Remember to check it before you post."
        : "Copy did not work. Press and hold the text to select and copy it.";
    }
    if (navigator.clipboard && window.isSecureContext) {
      navigator.clipboard.writeText(text).then(function () { done(true); }, function () { done(fallbackCopy(text)); });
    } else {
      done(fallbackCopy(text));
    }
  }

  function clearAll() {
    form.reset();
    Object.keys(fields).forEach(function (k) {
      fields[k].err.textContent = "";
      fields[k].el.removeAttribute("aria-invalid");
    });
    results.hidden = true;
    ["outHeadline", "outCaption", "outCta", "outTags"].forEach(function (id) {
      document.getElementById(id).textContent = "";
    });
    statusEl.textContent = "";
    window.scrollTo({ top: 0, behavior: "smooth" });
    fields.type.el.focus({ preventScroll: true });
  }

  form.addEventListener("submit", function (e) { e.preventDefault(); generate(true); });
  document.getElementById("clearBtn").addEventListener("click", clearAll);
  document.getElementById("copyBtn").addEventListener("click", copyAll);
  document.getElementById("againBtn").addEventListener("click", function () { generate(false); statusEl.textContent = "New version created."; });
  Object.keys(fields).forEach(function (k) {
    fields[k].el.addEventListener("input", function () {
      fields[k].err.textContent = "";
      fields[k].el.removeAttribute("aria-invalid");
    });
  });
})();
</script>
</body>
</html
