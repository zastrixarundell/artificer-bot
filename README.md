# Artificer

![Artificer Banner](https://raw.githubusercontent.com/zastrixarundell/artificer-bot/master/static_files/artificer-big-banner.jpg)
A Magical Bot for Discord Music

Note: The main image for the bot is from [here](https://www.artstation.com/artwork/v10g8x) and belongs to [Otto Metzger](https://ottometzger.artstation.com/) so do support their art!

## About

The bot is written in Elixir, a functional programming language based upon Erlang. It has great performance and maintainability in live environments.

The Discord library is [Nostrum](https://github.com/Kraigie/nostrum), written in Elixir and supporting everything from events to voice channels.

## Note regarding Nostrum

As of now the Hex release of Nostrum `v0.4.6` is a bit buggy so the current version of this bot uses the nightly version of Nostrum.

## System requirements

### Voice requirements

This bot needs `youtube-dl` and `ffmpeg` in order to play music. The path of them can be set with `FFMPEG_PATH` and `YTDL_PATH` accordingly. If they are not set they will back to `/usr/bin/ffmpeg/` and `/usr/bin/youtube-dl` accordingly. So if your `whereis <name>` returns those two, you don't need to worry about them.

### General bot requirements

Of course as this is written in Elixir, you will need Elixir and the BEAM systme installed. This can be easyly done on Debian-based distros:

```bash
sudo apt-get install elixir
```

After installing Elixir you should be able to see the version:

```bash
Erlang/OTP 23 [erts-11.1.7] [source] [64-bit] [smp:8:8] [ds:8:8:10] [async-threads:1] [hipe]

Elixir 1.11.2 (compiled with Erlang/OTP 23)
```

Try to keep the Elixir version `1.11.2` and up.

## Configuration

To set the bot up-and-running you will need to set a couple of variables.

Here's the basic configuration:

```elixir
use Mix.Config
config :porcelain,
  driver: Porcelain.Driver.Basic

config :nostrum,
  ffmpeg: System.get_env("FFMPEG_PATH") || "/usr/bin/ffmpeg",
  youtubedl: System.get_env("YTDL_PATH") || "/usr/bin/youtube-dl",
  token: System.get_env("DISCORD_BOT_TOKEN"),
  num_shards: :auto

config :artificer,
  prefix: System.get_env("DEFAULT_BOT_PREFIX")

```

Two required configs are `DISCORD_BOT_TOKEN` and `DEFAULT_BOT_PREFIX`.