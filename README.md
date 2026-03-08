# lite

a super small, singlefile game launcher for web games!

**Powered by UGS (Ultimate Games Stash).**

---

## x01 - Concepts

My friend and I love web games. I suppose it's a sort of thing we've developed over time from the elementary school days.

More and more however, I've wanted to have one place with all the games available. That's why I built the original Aeos line of game sites. And I figured, why not challenge myself with a trend at the time, which was to pack the site into one .html file that could run as a file: url.

## x02 - CORS

The first, immediate issue was CORS (Cross Origin Resource Sharing) restrictions. Because of a file: URL's unique setup when it comes to its origin (null), I needed to find a CDN that applied CORS headers such as Access-Control-Allow-Origin: *. I found a solution in jsDelivr, a CDN for GitHub and other services that applied the necessary CORS headers.

## x03 - Updates and Extendability

A major issue that came to mind was handling updates. If I simply shipped all the code in a .html file, it would be hard to update as users would have to download a new version every update. I fixed this issue by building a small launcher .html file that dynamically fetched the latest version from jsDelivr and injected the code into itself, creating a .html file that would automatically update with every new push.

## x04 - Where to get the games from?

Web games generally do not run natively in one .html file. Dependency and assets files are always involved. After some digging, I found UGS (Ultimate Games Stash), which, thanks to its contributors, had properly made web games function in one .html file by cleverly leveraging CDNs and other resources. Since UGS is a Google Doc and all games are placed in one Google Drive folder, I used Google's official Docs API and Drive API to set up a automated, dynamic fetching system that listed available games and injected their code.

## x05 - More browser security issues

Web games usually use browser features such as LocalStorage, Cookies, and IndexedDB. Most of these features do not work when directly injected onto a file url, or on about:blank. Initially, I thought using srcdoc would work to fix these issues, but it turns out some games (particularly games made outside of Unity) do not properly run in srcdoc. In the end, I used dynamic injection into about:blank, which worked to solve these issues for the vast majority of games.

## x06 - What's next?

Aeos Lite will likely not be updated past this point. While fixes will definitely be applied to issues to address issues that stop the code from working altogether, new features will likely not be added as I focus on new projects, especially a complete rewrite of Aeos, Aeos v4.
