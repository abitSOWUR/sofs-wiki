---
title: Game Developers
description: A list of game developers featured in this Wiki.
published: true
date: 2025-12-29T08:15:56.161Z
tags: 
editor: markdown
dateCreated: 2025-12-27T07:03:02.013Z
---

<div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 16px;">

  <!-- Aggro Crab -->
  <a href="/en/pages/developers/aggro-crab" style="text-decoration:none;">
    <div class="dev-card" data-dev-tag="dev:aggro-crab" style="border: 2.5px solid #ddd; border-radius: 8px; overflow: hidden;">
      <img src="/pages/assets/aggro crab cover.jpg" alt="Aggro Crab" style="width: 100%; aspect-ratio: 1/1; object-fit: cover;">
      <div style="padding: 8px; text-align: center;">
        <strong style="color:white">Aggro Crab</strong><br>
        <span class="dev-card-count" style="color:white">…</span>
      </div>
    </div>
  </a>

  <!-- Jackbox Games -->
  <a href="/en/pages/developers/Jackbox-Games" style="text-decoration:none;">
    <div class="dev-card" data-dev-tag="dev:jackbox-games" style="border: 2.5px solid #ddd; border-radius: 8px; overflow: hidden;">
      <img src="/pages/assets/jackbox_cover.jpg" alt="Jackbox Games" style="width: 100%; aspect-ratio: 1/1; object-fit: cover;">
      <div style="padding: 8px; text-align: center;">
        <strong style="color:white">Jackbox Games</strong><br>
        <span class="dev-card-count" style="color:white">…</span>
      </div>
    </div>
  </a>

  <!-- FromSoftware -->
  <a href="/en/pages/developers/FromSoftware" style="text-decoration:none;">
    <div class="dev-card" data-dev-tag="dev:fromsoftware" style="border: 2.5px solid #ddd; border-radius: 8px; overflow: hidden;">
      <img src="/pages/assets/fromsoftware cover.jpg" alt="FromSoftware" style="width: 100%; aspect-ratio: 1/1; object-fit: cover;">
      <div style="padding: 8px; text-align: center;">
        <strong style="color:white">FromSoftware</strong><br>
        <span class="dev-card-count" style="color:white">…</span>
      </div>
    </div>
  </a>

  <!-- Landfall Games -->
  <a href="/en/pages/developers/Landfall" style="text-decoration:none;">
    <div class="dev-card" data-dev-tag="dev:landfall" style="border: 2.5px solid #ddd; border-radius: 8px; overflow: hidden;">
      <img src="/pages/assets/landfall cover.jpg" alt="Landfall Games" style="width: 100%; aspect-ratio: 1/1; object-fit: cover;">
      <div style="padding: 8px; text-align: center;">
        <strong style="color:white">Landfall Games</strong><br>
        <span class="dev-card-count" style="color:white">…</span>
      </div>
    </div>
  </a>

</div>

<script>
document.addEventListener("DOMContentLoaded", () => {
  const cards = document.querySelectorAll(".dev-card[data-dev-tag]");
  if (!cards.length) return;

  function makeLabel(count) {
    if (count === 1) return "1 guide added";
    return count + " guides added";
  }

  cards.forEach(card => {
    const tag = card.getAttribute("data-dev-tag");
    const countEl = card.querySelector(".dev-card-count");
    if (!tag || !countEl) return;

    const query = `
      query($tag: String!) {
        pages(filter: { tags: [$tag] }) {
          total
        }
      }
    `;

    fetch("/graphql", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ query, variables: { tag } })
    })
    .then(res => res.json())
    .then(data => {
      const total = data && data.data && data.data.pages
        ? (data.data.pages.total || 0)
        : 0;

      countEl.textContent = makeLabel(total);
    })
    .catch(err => {
      console.error("Dev card count error:", err);
      countEl.textContent = "0 guides added";
    });
  });
});
</script>
