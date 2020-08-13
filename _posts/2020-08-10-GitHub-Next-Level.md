---
title: Let's bring your GitHub to the next level!
---
This is the try of bringing the GitHub to the next level. I am just curious where it ends up.

Based on tutorial available [here](https://www.youtube.com/watch?v=ECuqb5Tv9qI) and GitHub action tutorial [here](https://github.com/gautamkrishnar/blog-post-workflow)

And in my version it ends up in this [my repo], check it out!

Basically, interesting stuff is to define workflows (GitHub actions), and particular tasks are being executed automatically, based on defined schedule (for example, every 1 hour) or even triggered manually. In [my repo] there are examples of automatic update videos from Youtube (not mine, unfortunately), or posts from blog (not mine, unfortunately). Updated stuff is placed in [`README.md`](https://github.com/heniczyna/heniczyna/blob/master/README.md), and then available at GitHub profile, [here](https://github.com/heniczyna).

Let's consider this [section](https://github.com/heniczyna#star-gpw-gie%C5%82da-papier%C3%B3w-warto%C5%9Bciowych): this is about updating from GPW news. Workflow is defined in [gpw.yml](https://github.com/heniczyna/heniczyna/blob/master/.github/workflows/gpw.yml) as:
```
name: Latest GPW activity
on:
  schedule:
    # Runs every 5 minutes
    # - cron: '*/5 * * * *'
    # Runs every hour
    - cron: '0 * * * *'
  workflow_dispatch:

jobs:
  update-readme-with-gpw:
    name: Update this repo's README with latest GPW activity
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: gautamkrishnar/blog-post-workflow@master
        with:
          comment_tag_name: "GPW"
          commit_message: "Updated readme with the latest GPW data"
          feed_list: "https://www.gpw.pl/rss-news"
```
Every each hour GPW news are checked. If any changes occur, [`README.md`](https://github.com/heniczyna/heniczyna/blob/master/README.md) will be updated - corresponding section between tags:
```
<!-- GPW:START -->
<!-- GPW:END -->
```

All GitHub actions you can check in [Actions](https://github.com/heniczyna/heniczyna/actions) tab of your repo.

[my repo]: https://github.com/heniczyna/heniczyna
