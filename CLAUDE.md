# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## Project Overview

Single-file HTML vision test application using the Tumbling E chart method. No build tools or dependencies required.

## Quick Start

```bash
# Open directly in browser
open index.html

# Or serve locally
python3 -m http.server 8080
```

## Architecture

Single `index.html` file containing:
- Embedded CSS (mobile/PC/pad responsive design)
- Canvas-based E chart rendering
- JavaScript state machine for test flow (setup → preselect → test → result)

Key logic:
- `VISION_LEVELS` array: 14 acuity levels (4.0-5.3 score, 0.1-2.0 decimal)
- `DEVICE_CONFIG`: Calibration methods per device type
- Staircase testing algorithm: 3 questions per level, ≥2 correct passes

## Commands

```bash
# Deploy to production
sudo cp index.html /var/www/eye/html/
sudo nginx -s reload

# Verify deployment
curl -H "Host: eye.zhangtianle.cn" http://127.0.0.1/
```

## Deployment

- Domain: eye.zhangtianle.cn
- Web root: /var/www/eye/html
- Nginx config: /etc/nginx/sites-available/eye.conf

## Git

Remote: https://github.com/zhangtianle/eye_test