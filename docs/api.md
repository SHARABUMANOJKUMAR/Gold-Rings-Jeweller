# CALLA Jewellery Website - Architecture & API Documentation

## Overview
CALLA is a luxury fine jewellery interactive concept website with scrollytelling animations, canvas sequence rendering, interactive product customization, catalog filtering, wishlist, and shopping bag.

## Serving Layer (`tools/serve.mjs`)
A Node.js HTTP static server supporting byte-range streaming (for video and media assets):
- **Command**: `node tools/serve.mjs [rootDirectory] [port]`
- **Default Port**: `5533`
- **Root Directory**: `site`
- **Supported MIME Types**: `.html`, `.css`, `.js`, `.mjs`, `.json`, `.jpg`, `.png`, `.webp`, `.svg`, `.mp4`, `.woff2`, `.ico`
- **Streaming**: Supports `Range: bytes=start-end` (HTTP 206 Partial Content).

## Client Data & State Management
Client state is persisted in `localStorage` under keys prefixed with `calla:`:

### 1. Shopping Bag (`calla:bag`)
Stores items added by user:
```json
[
  {
    "id": "flora-ring",
    "name": "Flora Halo Ring",
    "price": 285000,
    "metal": "Yellow gold",
    "size": "52",
    "qty": 1
  }
]
```

### 2. Wishlist (`calla:wish`)
Stores item IDs saved by user:
```json
["flora-ring", "petal-hoops"]
```

