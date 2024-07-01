# YouTube Description Updater

This Python script automates the process of updating YouTube video descriptions using AI-generated content. It leverages the YouTube Data API and OpenAI's GPT models to create engaging, SEO-friendly descriptions for your videos.

## Features

- Fetch video information from a specified YouTube channel
- Generate AI-powered descriptions using OpenAI's GPT models
- Update video descriptions on YouTube
- Fetch and incorporate video transcripts (if available)
- Include customizable upsell links in descriptions
- Pause execution for user review between updates
- Force update option to refresh all descriptions

## Prerequisites

- Python 3.6 or higher
- Google Cloud project with YouTube Data API enabled
- OpenAI API key
- Required Python packages (see Installation section)

## Installation

1. Clone this repository or download the script.

2. Install the required Python packages:

```
pip install google-api-python-client openai youtube_transcript_api
```

3. Set up your API keys as environment variables (recommended) or prepare them for command-line input:

```
export YOUTUBE_API_KEY="your_youtube_api_key"
export OPENAI_API_KEY="your_openai_api_key"
```

## Usage

Basic usage:

```
python ytdesc.py --channel_id YOUR_CHANNEL_ID
```

### Command-line Arguments

- `--channel_id`: YouTube channel ID (required)
- `--category_id`: YouTube video category ID (default: 22)
- `--youtube_api_key`: YouTube Data API key (can be set via environment variable)
- `--openai_api_key`: OpenAI API key (can be set via environment variable)
- `--openai_model`: OpenAI model to use (default: "gpt-4")
- `--max_videos`: Maximum number of videos to process (default: 50)
- `--force_update`: Update all video descriptions, even if they already exist
- `--pause`: Pause after each video for user input
- `--upsell_links`: JSON string of upsell links to include in descriptions

### Examples

1. Update descriptions for all videos, pausing after each:

```
python ytdesc.py --channel_id YOUR_CHANNEL_ID --force_update --pause
```

2. Update descriptions with upsell links:

```
python ytdesc.py --channel_id YOUR_CHANNEL_ID --upsell_links '{"buy album": "http://amazon_link/", "listen on Spotify": "http://spotify_link"}'
```

3. Use a different OpenAI model and process only 10 videos:

```
python ytdesc.py --channel_id YOUR_CHANNEL_ID --openai_model "gpt-3.5-turbo" --max_videos 10
```

## Notes

- The script will skip videos that already have descriptions unless the `--force_update` flag is used.
- Transcript fetching requires the `youtube_transcript_api` package. If not installed, the script will run without fetching transcripts.
- Ensure your YouTube API quota is sufficient for the number of videos you're processing.
- The OpenAI API usage will incur costs based on your OpenAI plan and the model used.

## Troubleshooting

- If you encounter API key issues, ensure your environment variables are set correctly or provide the keys directly as command-line arguments.
- For any HTTP errors, check your internet connection and the validity of your API keys.
- If transcript fetching fails, it may be due to unavailable transcripts for specific videos. The script will continue without transcripts in such cases.

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to check [issues page](https://github.com/stimpy77/yt-desc-updater/issues) if you want to contribute.

## License

whatever