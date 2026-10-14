# AI Shorts Pipeline made via Python

First of all, I think we should start with flowchart that will represent the main idea of how does it work:

<img width="1600" height="710" alt="shorts_pipeline_flowchart" src="https://github.com/user-attachments/assets/62ea8c4a-eaea-4364-b647-9b74bab16dd3" />


<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1600 710" width="1600" height="710" font-family="Helvetica, Arial, sans-serif" xmlns:c2pa="http://c2pa.org/manifest"><metadata><c2pa:manifest>AAAWgmp1bWIAAAAeanVtZGMycGEAEQAQgAAAqgA4m3EDYzJwYQAAABZcanVtYgAAAEdqdW1kYzJtYQARABCAAACqADibcQN1cm46YzJwYTo2MDdhYTkyNS1hNThlLTQ0MzYtYWYyNy03MWU4M2RkNDUxMDcAAAADl2p1bWIAAAApanVtZGMyYXMAEQAQgAAAqgA4m3EDYzJwYS5hc3NlcnRpb25zAAAAALxqdW1iAAAARGp1bWRjYm9yABEAEIAAAKoAOJtxE2MycGEuaW5ncmVkaWVudC52MwAAAAAYYzJzaJvsuiT2Tt2ax1yqw1p3loMAAABwY2JvcqNpZGM6Zm9ybWF0bWltYWdlL3N2Zyt4bWxqaW5zdGFuY2VJRHgseG1wOmlpZDo1Y2I1NjhkMC1iYzYxLTQyZGMtYjdiNS1iYTRkZmFlOGM4NzNscmVsYXRpb25zaGlwaHBhcmVudE9mAAAB4mp1bWIAAABBanVtZGNib3IAEQAQgAAAqgA4m3ETYzJwYS5hY3Rpb25zLnYyAAAAABhjMnNox8G0aXt8BBuCofxr81I7QQAAAZljYm9yomdhY3Rpb25zgqJmYWN0aW9ua2MycGEub3BlbmVkanBhcmFtZXRlcnOha2luZ3JlZGllbnRzgaJjdXJseC1zZWxmI2p1bWJmPWMycGEuYXNzZXJ0aW9ucy9jMnBhLmluZ3JlZGllbnQudjNkaGFzaFggJa0x7lElpKM6JXBWJkVo7ukDhM2GsQe/oN+UUNlZY0CkZmFjdGlvbngdY29tLmFudGhyb3BpYy5jbGF1ZGUucHJvdmlkZWRqcGFyYW1ldGVyc6F4H2NvbS5hbnRocm9waWMub3JpZ2luLWNvbmZpZGVuY2VndW5rbm93bmtkZXNjcmlwdGlvbnhmQ2xhdWRlIHByb3ZpZGVkIHRoaXMgZmlsZSBhdCB0aGUgcmVxdWVzdCBvZiBhIHVzZXIgYW5kIG1heSBoYXZlIGNyZWF0ZWQgb3IgbW9kaWZpZWQgdGhlIGZpbGUgY29udGVudHMubXNvZnR3YXJlQWdlbnShZG5hbWVmQ2xhdWRlcmFsbEFjdGlvbnNJbmNsdWRlZPUAAADIanVtYgAAAEBqdW1kY2JvcgARABCAAACqADibcRNjMnBhLmhhc2guZGF0YQAAAAAYYzJzaDSEHzPO5ng1sMlzxn/GTY0AAACAY2JvcqVjYWxnZnNoYTI1NmNwYWRNAAAAAAAAAAAAAAAAAGRoYXNoWCCfuSysnLWH4fI6GuPoNnKaxfheiOQp4od3F/T25Lk1LmRuYW1lbmp1bWJmIG1hbmlmZXN0amV4Y2x1c2lvbnOBomVzdGFydBjDZmxlbmd0aBkeBAAAAj5qdW1iAAAAJ2p1bWRjMmNsABEAEIAAAKoAOJtxA2MycGEuY2xhaW0udjIAAAACD2Nib3KlY2FsZ2ZzaGEyNTZpc2lnbmF0dXJleE1zZWxmI2p1bWJmPS9jMnBhL3VybjpjMnBhOjYwN2FhOTI1LWE1OGUtNDQzNi1hZjI3LTcxZTgzZGQ0NTEwNy9jMnBhLnNpZ25hdHVyZWppbnN0YW5jZUlEeCx4bXA6aWlkOmFjNjkzYzk2LTM2NGEtNGQ4NS1hZDE4LWIwMmYwOWYxYjFkYnJjcmVhdGVkX2Fzc2VydGlvbnODomN1cmx4LXNlbGYjanVtYmY9YzJwYS5hc3NlcnRpb25zL2MycGEuaW5ncmVkaWVudC52M2RoYXNoWCAlrTHuUSWkozolcFYmRWju6QOEzYaxB7+g35RQ2VljQKJjdXJseCpzZWxmI2p1bWJmPWMycGEuYXNzZXJ0aW9ucy9jMnBhLmFjdGlvbnMudjJkaGFzaFggf2IczvTP+9PH97N54L6oGs243DLO1VOLurKAPhto+8WiY3VybHgpc2VsZiNqdW1iZj1jMnBhLmFzc2VydGlvbnMvYzJwYS5oYXNoLmRhdGFkaGFzaFggznskHHjzGeoTIGK6Rgv56zvcnJU6wSOePBlnBhjL4n90Y2xhaW1fZ2VuZXJhdG9yX2luZm+jZG5hbWVvQW50aHJvcGljIEZpbGVzZ3ZlcnNpb25lMS4wLjBrc3BlY1ZlcnNpb25lMi40LjAAABA4anVtYgAAAChqdW1kYzJjcwARABCAAACqADibcQNjMnBhLnNpZ25hdHVyZQAAABAIY2JvctKEWQISogEmGCFZAgowggIGMIIBjaADAgECAhRA5aAK7sI50L64g/oGQgU9Z1UTADAKBggqhkjOPQQDAzBJMRcwFQYDVQQKEw5BbnRocm9waWMsIFBCQzEuMCwGA1UEAxMlQW50aHJvcGljIENvbnRlbnQgQ3JlZGVudGlhbHMgUm9vdCBDQTAeFw0yNjA4MDcxODQzNTZaFw0yODA4MDYxOTQzNTZaMEQxFzAVBgNVBAoTDkFudGhyb3BpYywgUEJDMSkwJwYDVQQDEyBBbnRocm9waWMgQ2xhdWRlIENvbnRlbnQgU2lnbmluZzBZMBMGByqGSM49AgEGCCqGSM49AwEHA0IABJh6CmvLUBgFFNU0vUKlOVtE6djd17L5SuwX0LemFisBM3dkd/3cyjxFA3Qo5S46fX0/ihY0VZ7mfb9KF703t5OjWDBWMA4GA1UdDwEB/wQEAwIHgDAVBgNVHSUEDjAMBgorBgEEAYPoXgIBMAwGA1UdEwEB/wQCMAAwHwYDVR0jBBgwFoAUzlHiBIFOZFsj+OPEz5o+nMHXXMIwCgYIKoZIzj0EAwMDZwAwZAIwMXMdFJ4BetLLVY7ORuE9noqbbAZOZn/aArXyTwFAZfKrPzxF2vPoJNf1+UCdg1XGAjBwX1zd9WGqYkqmL5SFqw1QySjr1zJfpJM9+1rdDwSPLMOPOjKuiXjoU/pUUeG9RwmhY3BhZFkNngAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAPZYQK09B9S7daWjnsJehGmzKLxpdAyLKQJiLmgTk96+0IFoSFRwqos3/c1iXX1kNrLu7DO7B+Dr+o/q5cFOdWvlio4=</c2pa:manifest></metadata>
<defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="#111"/></marker></defs>
<rect width="1600" height="710" fill="#fff"/>
<text x="40" y="46" font-size="26" font-weight="700" fill="#111">Automated Shorts Pipeline</text>
<text x="40" y="70" font-size="14" fill="#666">Long video in, vertical Shorts out, with a human check before anything is published</text>
<rect x="40" y="140" width="270" height="470" rx="12" fill="none" stroke="#111" stroke-width="1.6"/>
<text x="60" y="171" font-size="13" font-weight="400" fill="#888" text-anchor="start">01</text>
<text x="86" y="171" font-size="15" font-weight="700" fill="#111" text-anchor="start">Input &amp; Ingestion</text>
<line x1="60" y1="184" x2="290" y2="184" stroke="#ccc" stroke-width="1"/>
<polyline points="310,375 350,375" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="350" y="140" width="270" height="470" rx="12" fill="none" stroke="#111" stroke-width="1.6"/>
<text x="370" y="171" font-size="13" font-weight="400" fill="#888" text-anchor="start">02</text>
<text x="396" y="171" font-size="15" font-weight="700" fill="#111" text-anchor="start">Speech-to-Text &amp; AI</text>
<line x1="370" y1="184" x2="600" y2="184" stroke="#ccc" stroke-width="1"/>
<polyline points="620,375 660,375" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="660" y="140" width="270" height="470" rx="12" fill="none" stroke="#111" stroke-width="1.6"/>
<text x="680" y="171" font-size="13" font-weight="400" fill="#888" text-anchor="start">03</text>
<text x="706" y="171" font-size="15" font-weight="700" fill="#111" text-anchor="start">Video Loop (per clip)</text>
<line x1="680" y1="184" x2="910" y2="184" stroke="#ccc" stroke-width="1"/>
<polyline points="930,375 970,375" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="970" y="140" width="270" height="470" rx="12" fill="none" stroke="#111" stroke-width="1.6"/>
<text x="990" y="171" font-size="13" font-weight="400" fill="#888" text-anchor="start">04</text>
<text x="1016" y="171" font-size="15" font-weight="700" fill="#111" text-anchor="start">Subtitles &amp; Packaging</text>
<line x1="990" y1="184" x2="1220" y2="184" stroke="#ccc" stroke-width="1"/>
<polyline points="1240,375 1280,375" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="1280" y="140" width="270" height="470" rx="12" fill="none" stroke="#111" stroke-width="1.6"/>
<text x="1300" y="171" font-size="13" font-weight="400" fill="#888" text-anchor="start">05</text>
<text x="1326" y="171" font-size="15" font-weight="700" fill="#111" text-anchor="start">Review &amp; Publishing</text>
<line x1="1300" y1="184" x2="1530" y2="184" stroke="#ccc" stroke-width="1"/>
<rect x="60" y="200" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="74" y="224" font-size="13" font-weight="700" fill="#111" text-anchor="start">Download</text>
<text x="74" y="244" font-size="12" font-weight="400" fill="#555" text-anchor="start">yt-dlp, up to 1080p,</text>
<text x="74" y="260" font-size="12" font-weight="400" fill="#555" text-anchor="start">saved to local disk</text>
<polyline points="175.0,270 175.0,294" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="60" y="294" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="74" y="318" font-size="13" font-weight="700" fill="#111" text-anchor="start">Audio extraction</text>
<text x="74" y="338" font-size="12" font-weight="400" fill="#555" text-anchor="start">Clean audio track for analysis</text>
<rect x="370" y="200" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="384" y="224" font-size="13" font-weight="700" fill="#111" text-anchor="start">Transcription</text>
<text x="384" y="244" font-size="12" font-weight="400" fill="#555" text-anchor="start">Whisper (local), word-level</text>
<text x="384" y="260" font-size="12" font-weight="400" fill="#555" text-anchor="start">timestamps</text>
<polyline points="485.0,270 485.0,294" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="370" y="294" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="384" y="318" font-size="13" font-weight="700" fill="#111" text-anchor="start">Analysis</text>
<text x="384" y="338" font-size="12" font-weight="400" fill="#555" text-anchor="start">GPT-4o finds complete dialogues</text>
<text x="384" y="354" font-size="12" font-weight="400" fill="#555" text-anchor="start">and emotional moments</text>
<polyline points="485.0,364 485.0,388" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="370" y="388" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="384" y="412" font-size="13" font-weight="700" fill="#111" text-anchor="start">JSON output</text>
<text x="384" y="432" font-size="12" font-weight="400" fill="#555" text-anchor="start">start, end, title, hashtags</text>
<rect x="680" y="200" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="694" y="224" font-size="13" font-weight="700" fill="#111" text-anchor="start">Trimming</text>
<text x="694" y="244" font-size="12" font-weight="400" fill="#555" text-anchor="start">Cut the scene via MoviePy / FFmpeg</text>
<polyline points="795.0,270 795.0,294" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="680" y="294" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="694" y="318" font-size="13" font-weight="700" fill="#111" text-anchor="start">Silence removal</text>
<text x="694" y="338" font-size="12" font-weight="400" fill="#555" text-anchor="start">Cut gaps longer than 1.5 s</text>
<text x="694" y="354" font-size="12" font-weight="400" fill="#555" text-anchor="start">using word timestamps</text>
<polyline points="795.0,364 795.0,388" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="680" y="388" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="694" y="412" font-size="13" font-weight="700" fill="#111" text-anchor="start">Face tracking crop</text>
<text x="694" y="432" font-size="12" font-weight="400" fill="#555" text-anchor="start">OpenCV + MediaPipe, dynamic</text>
<text x="694" y="448" font-size="12" font-weight="400" fill="#555" text-anchor="start">9:16 vertical reframe</text>
<polyline points="795.0,458 795.0,482" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="680" y="482" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="694" y="506" font-size="13" font-weight="700" fill="#111" text-anchor="start">Uniqueness filters</text>
<text x="694" y="526" font-size="12" font-weight="400" fill="#555" text-anchor="start">Light color grade, +3% speed,</text>
<text x="694" y="542" font-size="12" font-weight="400" fill="#555" text-anchor="start">slow zoom-in at the end</text>
<rect x="990" y="200" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1004" y="224" font-size="13" font-weight="700" fill="#111" text-anchor="start">Subtitles</text>
<text x="1004" y="244" font-size="12" font-weight="400" fill="#555" text-anchor="start">1-3 words at a time, centered,</text>
<text x="1004" y="260" font-size="12" font-weight="400" fill="#555" text-anchor="start">synced to Whisper timestamps</text>
<polyline points="1105.0,270 1105.0,294" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<rect x="990" y="294" width="230" height="70" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1004" y="318" font-size="13" font-weight="700" fill="#111" text-anchor="start">Packaging</text>
<text x="1004" y="338" font-size="12" font-weight="400" fill="#555" text-anchor="start">Video + title + description +</text>
<text x="1004" y="354" font-size="12" font-weight="400" fill="#555" text-anchor="start">Fair Use disclaimer</text>
<rect x="1300" y="200" width="230" height="60" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1314" y="224" font-size="13" font-weight="700" fill="#111" text-anchor="start">Moderation</text>
<text x="1314" y="244" font-size="12" font-weight="400" fill="#555" text-anchor="start">Draft sent to Telegram bot</text>
<polyline points="1415.0,260 1415.0,282" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<polygon points="1415.0,282 1475.0,318 1415.0,354 1355.0,318" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1415.0" y="322" font-size="12" font-weight="700" fill="#111" text-anchor="middle">Approve?</text>
<polyline points="1415.0,354 1415.0,372" fill="none" stroke="#111" stroke-width="1.5"/>
<polyline points="1354,372 1476,372" fill="none" stroke="#111" stroke-width="1.5"/>
<polyline points="1354,372 1354,392" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<polyline points="1476,372 1476,392" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<text x="1348" y="366" font-size="11" font-weight="400" fill="#555" text-anchor="end">yes</text>
<text x="1482" y="366" font-size="11" font-weight="400" fill="#555" text-anchor="start">no</text>
<rect x="1300" y="392" width="108" height="90" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1354.0" y="416" font-size="13" font-weight="700" fill="#111" text-anchor="middle">Auto-post</text>
<text x="1354.0" y="436" font-size="11" font-weight="400" fill="#555" text-anchor="middle">Playwright,</text>
<text x="1354.0" y="452" font-size="11" font-weight="400" fill="#555" text-anchor="middle">cookie login,</text>
<text x="1354.0" y="468" font-size="11" font-weight="400" fill="#555" text-anchor="middle">YouTube / TikTok</text>
<rect x="1422" y="392" width="108" height="90" rx="6" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1476.0" y="416" font-size="13" font-weight="700" fill="#111" text-anchor="middle">Delete</text>
<text x="1476.0" y="436" font-size="11" font-weight="400" fill="#555" text-anchor="middle">Clean up</text>
<text x="1476.0" y="452" font-size="11" font-weight="400" fill="#555" text-anchor="middle">temp files</text>
<polyline points="1354,482 1354,500" fill="none" stroke="#111" stroke-width="1.5"/>
<polyline points="1476,482 1476,500" fill="none" stroke="#111" stroke-width="1.5"/>
<polyline points="1354,500 1476,500" fill="none" stroke="#111" stroke-width="1.5"/>
<polyline points="1415.0,500 1415.0,516" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<polygon points="1415.0,516 1477.0,550 1415.0,584 1353.0,550" fill="#fff" stroke="#111" stroke-width="1.3"/>
<text x="1415.0" y="554" font-size="12" font-weight="700" fill="#111" text-anchor="middle">More clips?</text>
<polyline points="1415.0,584 1415.0,650" fill="none" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
<text x="1423.0" y="624" font-size="11" font-weight="400" fill="#555" text-anchor="start">no</text>
<rect x="1365.0" y="650" width="100" height="34" rx="17.0" fill="#111"/>
<text x="1415.0" y="671.5" font-size="13" font-weight="600" fill="#fff" text-anchor="middle">End</text>
<polyline points="1353.0,550 1260,550 1260,640 795.0,640 795.0,610" fill="none" stroke="#111" stroke-width="1.5" stroke-dasharray="6 5" marker-end="url(#ar)"/>
<text x="1105.0" y="632" font-size="12" font-weight="400" fill="#555" text-anchor="middle">yes: next clip</text>
<rect x="40" y="90" width="150" height="32" rx="16.0" fill="#111"/>
<text x="115.0" y="110.5" font-size="13" font-weight="600" fill="#fff" text-anchor="middle">Start: video URL</text>
<line x1="115" y1="122" x2="115" y2="140" stroke="#111" stroke-width="1.5" marker-end="url(#ar)"/>
</svg>
