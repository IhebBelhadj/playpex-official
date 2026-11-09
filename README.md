# Playpex plugins

The official plugin repository of [Playpex Media Server](https://github.com/IhebBelhadj/Playpex). Every server has it built in (Plugins › Browse on its dashboard): its address and key ship with the server. It never carries a plugin for adults only.

| Plugin | What it does |
|---|---|
| `trakt` (Trakt) | scrobbles what a profile watches, keeps its watch list, history and ratings in sync with a Trakt account, adds Trakt's rating and rows to title pages and sections |
| `m3u` (Live TV (M3U)) | the channels of an M3U playlist the admin gives (their IPTV subscription or a public list) with their XMLTV programme guide, in a Live TV section; carries no list of its own |
| `youtube` (YouTube) | YouTube on the big screen: trending and category rows, search, channels and playlists through the YouTube Data API (the admin's key), a linked Google account's subscriptions, liked videos and playlists (read-only); videos play in YouTube's own player under Playpex's controls. Needs Playpex Media Server with plugin API 1.3 |

## Checking it

The index is `https://ihebbelhadj.github.io/playpex-official/index.json`, signed (`index.json.sig`) with the key `ed25519:jwgCJg+cIkeB3780604xy4dhMrngT4h4NJrT2Nas2cw=` (fingerprint `1440 8b9d b5d7 cf14 eac7 2c7b c4ea 0738`). The packages are signed with it too: a server trusting the key installs them by upload.

## Building it

From the Playpex repository, after changing a plugin (raise its `version`):

```
npm run pack:repository -- plugins/<plugin> --out ~/projects/playpex-plugins/official \
  --key ~/projects/playpex-keys/official.json --id playpex --name "Playpex" \
  --base-url https://ihebbelhadj.github.io/playpex-official/ --sign-packages
```

Then commit and push this folder; GitHub Pages serves it.
