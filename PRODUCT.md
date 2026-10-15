# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Static HTML/CSS/JS in a single `index.html` (user preference: "si se puede hacer bien con HTML, CSS y JavaScript, prefiero un único archivo"). No build step. Deployed to Cloudflare Pages (project `demo-gym`) from GitHub `AleexX26/demo-gym`.

## Users

- Primary (of the demo): owners of independent neighbourhood gyms and CrossFit-style boxes in Spain, shown this site as a sales demo. It must impress in the first five seconds.
- Primary (inside the demo): a person from the neighbourhood who wants to start training (often a beginner or someone returning), checking schedule, coaches, prices and how to try it for free.

## Product Purpose

A fictional neighbourhood gym (strength, coached group classes, personal training) whose website pushes every visitor to book a free trial class without friction. Success: the visitor finds a class or plan that fits and sends a pre-filled WhatsApp/email request.

## Positioning

Small, independent, with character: technique before load, small groups, no posturing. Coaches know members by name. (Inferred from the brief; gym identity is fictional.)

## Operating Context

Weekly class timetable by discipline (Fuerza, HIIT, Cross training, Boxeo, Yoga, Movilidad), 3 coaches, 4 membership plans with closed prices, free trial → initial assessment → tailored plan → first month → follow-up. No backend: booking produces a WhatsApp message or email.

## Capabilities and Constraints

- All data (gym, coaches, classes, plans) in plain arrays at the top of the code; filters generated from data.
- Missing images fall back to SVG illustrations in the site style.
- Real photographs only from free commercial-use sources (Unsplash/Pexels), downloaded into the project; no bodybuilder stock imagery (user decision 2026-10-15).
- Light and dark mode following the system; reduced-motion respected; Spanish copy.
- Gym name, city, email, WhatsApp, Instagram: invented by Claude (user decision 2026-10-15).

## Brand Commitments

None real; the gym is fictional. Brief bans: neon, lightning bolts, flames, glass, gradients, emoji, generic icon cards.

## Evidence on Hand

No real testimonials, member counts, press or reviews. Do not fabricate them.

## Product Principles

- Everything leads to the free trial.
- Information a newcomer needs (schedule, price, what to bring) is never hidden.
- Warm and welcoming to beginners, with character; never intimidating.
- Easy for a non-developer to edit data without touching design.
