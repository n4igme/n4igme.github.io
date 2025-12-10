# n4igme.github.io

Welcome to the repository for [n4igme.github.io](https://n4igme.github.io), a personal website and blog showcasing various tools, projects, and resources related to cybersecurity, technology, and more.

## Table of Contents

- [About](#about)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About

This repository contains the source code for my personal website, hosted on GitHub Pages. The website includes information about various projects, tools, and articles related to cybersecurity and technology.

## Features

- **Project Showcases**: Detailed descriptions of various cybersecurity tools and resources.
- **Blog Posts**: Articles on different topics related to technology and cybersecurity.
- **Interactive Elements**: Links to external resources and tools.
- **Fixed External Navigation**: Proper handling of external links in navigation menu to ensure they work correctly.

## Technical Updates

### Fixed External Link Issue (December 2025)
- **Problem**: External links in navigation menu weren't redirecting properly due to JavaScript interference
- **Root Cause**: The `main.js` file was applying the `scrolly` class and special event handlers to all navigation links, including external ones
- **Solution**: Modified navigation handling to distinguish between internal (`#anchor`) and external links, ensuring external links function normally without JavaScript interference
- **Files Updated**:
  - `_layouts/default.html` - Navigation structure
  - `assets/js/main.js` - JavaScript logic for navigation handling

## Installation

This project uses Jekyll and GitHub Pages to host the site. To run this site locally, follow these steps:

1. **Clone the Repository**

   ```bash
   git clone https://github.com/n4igme/n4igme.github.io.git
   ```

2. **Navigate to the Project Directory**

   ```bash
   cd n4igme.github.io
   ```

3. **Install Jekyll and Dependencies**

   ```bash
   # Install Ruby if you don't have it
   # Install Jekyll and Bundler gems
   gem install jekyll bundler
   # Install dependencies from Gemfile
   bundle install
   ```

4. **Serve the Site Locally**

   ```bash
   # Build and serve the site with auto-reload
   bundle exec jekyll serve
   ```

   The site will be available at `http://localhost:4000`

## Contributing

Contributions to improve the site are welcome. To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

## License

This project is licensed under the Creative Commons Attribution 4.0 International License - see the [LICENSE.md](LICENSE.md) file for details.

## Contact

- **Email**: [n4igme@gmail.com](mailto:n4igme@gmail.com)
- **GitHub**: [n4igme](https://github.com/n4igme)
- **Website**: [n4igme.github.io](https://n4igme.github.io)