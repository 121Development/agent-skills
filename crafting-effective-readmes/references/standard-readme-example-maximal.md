# Widget Pro

> Enterprise widget formatting with plugins, caching, and monitoring

[![Build Status](https://img.shields.io/badge/build-passing-green)]()

## Description

Widget Pro formats widgets at scale. It handles edge cases that the basic widget formatter misses: nested widgets, internationalization, and custom schemas.

## Features

- Plugin architecture
- LRU caching
- Prometheus metrics
- JSON Schema validation

## Installation

```bash
npm install widget-pro
```

## Quick Start

```javascript
const WidgetPro = require('widget-pro');
const formatter = new WidgetPro({ cache: true });
const result = await formatter.format(widgetData);
```

## Configuration

See [CONFIG.md](CONFIG.md) for full options.

## API

### `new WidgetPro(options)`

Creates a formatter instance.

### `format(data)`

Formats widget data. Returns a Promise.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)

## License

MIT © [Author]
