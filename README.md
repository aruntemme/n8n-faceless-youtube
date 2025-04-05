# YouTube Faceless Video Automation with n8n

A comprehensive solution for automating the creation and uploading of faceless YouTube videos using n8n workflows.

## Overview

This repository contains an n8n workflow that automates the process of creating faceless YouTube videos. The workflow pulls content from Google Sheets (quotes, stock videos, and music), assembles them into a video, and uploads it directly to YouTube - all without requiring manual video editing.

## Prerequisites

- Docker installed on your system
- Google account for YouTube uploads and Google Sheets
- Google API credentials
- Basic understanding of n8n workflows

## Installation

### Step 1: Check Docker Installation

Before proceeding, ensure Docker is installed on your system:

```bash
docker --version
```

If Docker is not installed, please follow the [official Docker installation guide](https://docs.docker.com/get-docker/) for your operating system.

### Step 2: Install n8n Using Docker

1. Create a Docker volume to store persistent data:

```bash
docker volume create n8n_data
```

2. Run n8n in a Docker container:

```bash
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

3. Access n8n by opening your browser and navigating to:
```
http://localhost:5678
```

## Setting Up the Workflow

### Step 1: Import the Workflow

1. Download the `Youtube_video_no_voice_automation.json` file from this repository
   - [Direct link to workflow file](./Youtube_video_no_voice_automation.json)
2. In the n8n interface, click on **Workflows** in the sidebar
3. Click the **Import from File** button (or **Import from URL** if accessing the workflow from a direct link)
4. Select the downloaded `Youtube_video_no_voice_automation.json` file
5. Click **Import** to load the workflow into n8n

### Step 2: Configure Google API Credentials

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing project
3. Enable the following APIs:
   - Google Sheets API
   - YouTube Data API v3
4. Create OAuth 2.0 credentials with the following scopes:
   - `https://www.googleapis.com/auth/spreadsheets`
   - `https://www.googleapis.com/auth/youtube.upload`
   - `https://www.googleapis.com/auth/youtube`

### Step 3: Add Credentials to n8n

1. In n8n, go to the **Credentials** section
2. Add new Google Sheets credentials:
   - Click **Create New**
   - Select **OAuth2 API**
   - Enter the Client ID and Client Secret from your Google Cloud Console
   - Follow the authorization process
3. Add new YouTube credentials:
   - Click **Create New**
   - Select **OAuth2 API**
   - Enter the Client ID and Client Secret from your Google Cloud Console
   - Follow the authorization process

### Step 4: Set Up Google Sheets

A sample `template.xlsx` file is included in this repository. Import this file into Google Sheets and use it as a template.

The sheet contains the following structure:

1. **Video Logs**: Collection of quotes to use in your videos and the logs of the videos uploaded
2. **Video Pools**: Collection of stock videos
3. **Music Pools**: Collection of background music

Share the Google Sheet with the email associated with your Google API credentials.

## Video Tutorial

For a visual guide on setting up and using this workflow, check out this helpful tutorial:
[YouTube Faceless Video Automation Tutorial](https://www.youtube.com/watch?v=9ZGa7sw9ZYA&t=25s)

Note: This tutorial is in Tamil language and demonstrates the output of the automation rather than the entire workflow setup. It provides a good visualization of what can be achieved with this tool.

## Usage

1. Update the workflow configuration with your Google Sheet ID
2. Configure the YouTube upload settings in the workflow
3. Activate the workflow
4. Execute the workflow manually or set a trigger (time-based, webhook, etc.)

The workflow will:
1. Fetch a random quote from your quotes sheet
2. Select appropriate stock video based on category matching
3. Choose background music
4. Assemble the video with text overlay
5. Upload the completed video to YouTube with proper metadata

## Customization

You can customize various aspects of the workflow:
- Video resolution and quality
- Text overlay style and positioning
- Video duration
- Upload schedule
- Auto-generated titles and descriptions

## Troubleshooting

If you encounter any issues:

1. Check the n8n logs for error messages
2. Verify your Google API credentials have the necessary permissions
3. Ensure your Google Sheet is properly structured and accessible
4. Check network connectivity for accessing YouTube and Google services

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [n8n](https://n8n.io/) for providing the workflow automation platform
- [YouTube Data API](https://developers.google.com/youtube/v3) for video upload capabilities

---

⭐ If you find this workflow useful, please star the repository!