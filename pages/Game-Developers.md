---
title: Game Developers
description: A list of game developers featured in this Wiki.
published: true
date: 2025-12-29T09:44:16.178Z
tags: 
editor: markdown
dateCreated: 2025-12-27T07:03:02.013Z
---

[

![Aggro Crab](/pages/assets/aggro crab cover.jpg)

**Aggro Crab**  
…



](/en/pages/developers/aggro-crab)[

![Jackbox Games](/pages/assets/jackbox_cover.jpg)

**Jackbox Games**  
…



](/en/pages/developers/Jackbox-Games)[

![FromSoftware](/pages/assets/fromsoftware cover.jpg)

**FromSoftware**  
…



](/en/pages/developers/FromSoftware)[

![Landfall Games](/pages/assets/landfall cover.jpg)

**Landfall Games**  
…



](/en/pages/developers/Landfall)

(function() { const cards = document.querySelectorAll(".dev-card\[data-dev-tag\]"); if (!cards.length) return; function makeLabel(count) { if (count === 1) return "1 guide added"; return count + " guides added"; } cards.forEach(card => { const tag = card.getAttribute("data-dev-tag"); const countEl = card.querySelector(".dev-card-count"); if (!tag || !countEl) return; const query = \` query($tag: String!) { pages(filter: { tags: \[$tag\] }) { total } } \`; fetch("/graphql", { method: "POST", headers: { "Content-Type": "application/json" }, body: JSON.stringify({ query, variables: { tag } }) }) .then(res => res.json()) .then(data => { const total = data && data.data && data.data.pages ? (data.data.pages.total || 0) : 0; countEl.textContent = makeLabel(total); }) .catch(err => { console.error("Dev card count error:", err); countEl.textContent = "0 guides added"; }); }); })();