# Cloudflare Pages Deployment Cleanup
A Node.js utility script to automatically list and delete older Cloudflare Pages deployments for a project while safeguarding the live production deployment.
## Features
 * Production Safeguard: Automatically fetches and protects the active production deployment from being deleted.
 * Pagination Support: Fetches all historical deployments sequentially using safe pagination.
 * Resiliency: Implements exponential backoff to handle API rate limiting smoothly.
 * Optional Alias Deletion: Can be configured to force-delete deployments that have active preview aliases.
## Prerequisites
 * Node.js (v18 or higher recommended)
 * A Cloudflare account with a Pages project configured.
 * A Cloudflare API Token with permissions to read and edit Pages projects.
## Installation
 1. Clone or download this repository to your local machine.
 2. Navigate to the project directory and install the required dependencies:
npm install node-fetch exponential-backoff dotenv
## Configuration
Create a .env file in the root of your project directory and populate it with your Cloudflare credentials:
CF_API_TOKEN=
CF_ACCOUNT_ID=
CF_PAGES_PROJECT_NAME=
CF_DELETE_ALIASED_DEPLOYMENTS=false
### Environment Variables Glossary
 * CF_API_TOKEN: Your Cloudflare API token (Requires Pages Read/Write permissions).
 * CF_ACCOUNT_ID: Your Cloudflare Account ID.
 * CF_PAGES_PROJECT_NAME: The exact name of your Cloudflare Pages project.
 * CF_DELETE_ALIASED_DEPLOYMENTS: Set to true to force-delete deployments with associated preview aliases. Set to false to skip them.
## Usage
Run the script using Node.js:
node index.js
Warning: This script permanently deletes deployments. Ensure your .env settings—especially CF_DELETE_ALIASED_DEPLOYMENTS—are configured correctly before running.
