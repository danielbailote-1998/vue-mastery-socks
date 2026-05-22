# Vue Mastery Socks 🧦

A simple Vue 3 product page built with the Composition API. Users can browse sock variants, submit reviews, and add items to a cart.

---

## Preview

<img width="1240" height="1190" alt="vue-socks" src="https://github.com/user-attachments/assets/e9097c6d-6a04-4d1a-8545-991d920f32b5" />

---

## Features

- Product variant switching (green / blue socks) with live image update
- In-stock / out-of-stock indicator per variant
- Dynamic shipping cost based on premium membership
- Add to cart with variant tracking
- Review form with name, rating, and comment
- Review list rendered conditionally when reviews exist

---

## Project Structure

```
frontend/
├── public/
│   ├── favicon.svg
│   └── icons.svg
├── src/
│   ├── assets/
│   │   └── images/
│   │       ├── socks_green.jpeg
│   │       └── socks_blue.jpeg
│   ├── components/
│   │   ├── ProductDisplay.vue   # Main product card, variant logic, cart emit
│   │   ├── ReviewForm.vue       # Form to submit a new review
│   │   └── ReviewList.vue       # Displays submitted reviews
│   ├── App.vue                  # Root component, cart state, premium flag
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
└── vite.config.js
```

---

## Getting Started

**Prerequisites:** Node.js 18+

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

---

## Components

### `App.vue`
Root component. Holds the `cart` array and `premium` boolean. Listens for the `add-to-cart` event from `ProductDisplay` and pushes the variant ID into the cart.

### `ProductDisplay.vue`
Receives `premium` as a prop. Computes the product title, active image, stock status, and shipping cost. Emits `add-to-cart` on button click. Renders `ReviewForm` and `ReviewList` as children.

### `ReviewForm.vue`
Reactive form with name, review text, and star rating (1–5). Validates all fields before emitting `review-submitted` to the parent. Resets after submission.

### `ReviewList.vue`
Accepts a `reviews` array prop and renders each entry with the reviewer's name, rating, and comment text.

---

## Props & Events

| Component | Prop | Type | Description |
|---|---|---|---|
| `ProductDisplay` | `premium` | Boolean | Toggles free vs paid shipping |
| `ReviewList` | `reviews` | Array | List of review objects to display |

| Component | Event | Payload | Description |
|---|---|---|---|
| `ProductDisplay` | `add-to-cart` | variant ID | Fired when the cart button is clicked |
| `ReviewForm` | `review-submitted` | `{ name, content, rating }` | Fired on valid form submission |

---

## Tech Stack

- [Vue 3](https://vuejs.org/) — Composition API with `<script setup>`
- [Vite](https://vitejs.dev/) — Dev server and build tool
