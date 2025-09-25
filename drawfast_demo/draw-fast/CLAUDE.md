# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- `npm install` - Install dependencies
- `npm run dev` - Start development server (Next.js)
- `npm run build` - Build production version
- `npm start` - Start production server
- `npm run lint` - Run ESLint
- `npm run format` - Format code with Prettier

## Project Architecture

This is a **Draw Fast** demo application that combines tldraw with real-time AI image generation using the Fal.ai API. The app allows users to draw in a frame and see AI-generated images based on their drawings and text prompts.

### Core Architecture

**Next.js App Router Structure:**
- `src/app/page.tsx` - Main application page with Tldraw editor setup
- `src/app/api/fal/proxy/route.ts` - API proxy for Fal.ai requests
- `src/app/layout.tsx` - Root layout component

**Custom Tldraw Integration:**
- `src/components/LiveImageShapeUtil.tsx` - Custom shape utility that extends tldraw's frame functionality
- `src/components/LiveImageTool.tsx` - Custom tool for creating live image frames
- `src/hooks/useLiveImage.tsx` - Core hook that manages the drawing-to-image generation pipeline

### Key Concepts

**LiveImage Shape:**
- A custom tldraw shape that extends the frame concept
- Captures drawings within its bounds and sends them to AI for image generation
- Supports overlay mode to show generated images over or beside the drawing area

**Real-time Pipeline:**
1. User draws shapes within a LiveImage frame
2. `useLiveImage` hook detects changes and captures SVG of touching shapes
3. SVG is converted to JPEG using `fastGetSvgAsImage` utility
4. Image and prompt are sent to Fal.ai's LCM (Latent Consistency Model) API
5. Generated image is stored as a tldraw asset and displayed

**Fal.ai Integration:**
- Uses `@fal-ai/serverless-client` for real-time WebSocket connections
- Configured with custom proxy at `/api/fal/proxy`
- Default app ID: `110602490-lcm-sd15-i2i` (image-to-image model)

### Environment Setup

Requires `FAL_KEY` environment variable with a valid Fal.ai API key. See README.md for setup instructions.

### Utilities

- `src/utils/screenshot.ts` - SVG to image conversion utilities
- `src/utils/debounce.ts` - Debouncing helper functions
- `src/utils/blob.ts` - Blob manipulation utilities

### Important Implementation Details

- The app patches tldraw's `isShapeOfType` method to make live-image shapes behave like frames
- Uses tldraw's asset system to store and display generated images
- Implements throttling and timeout mechanisms for API requests
- Supports both overlay and side-by-side display modes for generated images