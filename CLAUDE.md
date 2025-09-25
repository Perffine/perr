# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website repository for perr.ca, serving as a personal portfolio and landing page for software projects. The site showcases Chrome extensions, games, and other applications developed by the project owner.

## Architecture

The repository follows a simple static website structure:

- **Root level**: Contains the main `index.html` landing page, shared `style.css`, and domain configuration files
- **Project subdirectories**: Each software project has its own folder (`sidepanelCalendar/`, `yt-com/`, `yt-sum/`) containing:
  - `explanation.html` - Technical documentation and feature explanation
  - `priv.html` - Privacy policy
  - `tou.html` - Terms of use/conditions
- **im_dead/**: Contains personal documents (handle with appropriate sensitivity)

## Key Projects Featured

1. **Victor's Calendar Program** (`sidepanelCalendar/`) - Chrome extension for Google Calendar integration
2. **YouTube Comment Analyzer** (`yt-com/`) - Chrome extension for analyzing YouTube comments using ChatGPT API
3. **YouTube Summarizer** (`yt-sum/`) - Chrome extension for YouTube video summarization with bias detection

Note: The `yt-sum/` project appears to be called "yu2bias" in its explanation page and includes bias analysis functionality using ChatGPT4o-mini and Google custom search.

## Development Commands

This is a static website with no build system. Files are served directly:

- **Local development**: Open `index.html` in a browser or use any static file server (e.g., `python -m http.server` or `npx serve .`)
- **Deployment**: Files are served via GitHub Pages (configured with CNAME for perr.ca domain)

## Website Configuration

- **Domain**: Configured via `CNAME` file for perr.ca
- **SEO**: `robots.txt` allows Googlebot access while blocking other crawlers
- **Responsive design**: CSS includes mobile-specific media queries for screens under 600px width

## Content Guidelines

- All HTML files use shared `style.css` for consistent styling
- Links maintain consistent formatting with hover effects using CSS transitions
- Each project maintains separate documentation pages for compliance and transparency
- Privacy policies reference Google API Services User Data Policy compliance
- Project explanation pages include technical details about API usage and data handling