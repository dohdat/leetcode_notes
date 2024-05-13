# Design Youtube

## Requirements
### Functional requirements
1. Users should be able to upload videos.
2. Users should be able to share and view videos.
3. Users should be able to perform searches based on video titles.
4. Our services should be able to record stats of videos, e.g., likes/dislikes, total number of views,
etc.
5. Users should be able to add and view comments on videos.
### Non-functional requirements
1. The system should be highly reliable, any video uploaded should not be lost.
2. The system should be highly available. Consistency can take a hit (in the interest of
availability); if a user doesn’t see a video for a while, it should be fine.
3. Users should have a real time experience while watching videos and should not feel any lag.

## Capacity estimation and constraints

- **Total users:** 1.5 billion, with 800 million daily active users.
- **Daily video views:** Estimated at 46,000 videos per second based on an average of 5 views per user per day.
- Upload:view ratio: Assumed to be 1:200, resulting in 230 videos uploaded per second.
- **Storage needs:** With 500 hours of video uploaded per minute, and assuming 50MB of storage per minute of video, the storage requirement amounts to 1500 GB/min (25 GB/sec).
- **Bandwidth requirements:** Anticipated outgoing bandwidth of 1TB/s considering 300GB of uploads every minute and a 1:200 upload:view ratio.

