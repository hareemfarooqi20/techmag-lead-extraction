# techmag-lead-extraction

Backup lead-extraction workflow for Tech Mag Solutions. Public repo so
the extraction cron gets unlimited free GitHub Actions minutes.

This repo contains **only workflow/CI configuration** - no business data,
no prospect data, no credentials. Each run checks out the private
`techmagsolutions` repo (via a scoped fine-grained PAT stored as the
`PRIVATE_REPO_PAT` secret), runs the Overpass-based hunt scripts there,
and pushes results straight back to that private repo. Nothing extracted
is ever committed here.

Primary extraction still runs locally (Windows Task Scheduler + Docker,
10 PM-7 AM daily) using self-hosted Overpass containers. This workflow is
a secondary/backup source using the public Overpass API, in case the
local machine is off or the task doesn't run.
