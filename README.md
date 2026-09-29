JobTracker written with React using Supabase
This directory based on the brief example of a Create React App site that can be deployed to Vercel with zero configuration.

However, this specific build is customized to my own needs. This includes, tracking specific details of each application like user access, authentication, authorization, URL, notes, dates, status, salary, etc. To this end I required a cloud database, cloud app hosting, multiple environments for testing, mobile access, and encryption.

The tools I used included React/NextJs for coding, Vercel for secure app cloud hosting, Supabase for cloud database, user management and password changes and finally, authentication and authorization. Cost was also an issue and I used the free platforms as much as possible.

My app URL
I deployed my own React App project with Vercel here:

https://readonlyjobtracker.vercel.app/

Files
Thid document will be updated to properly document the different start and build commands. There are a number of configurations necessary to connect to Supabase as well as Vercel to connect to Github to push the code updates automatically.

Diagram
Below is the infrastructure: 

                 ┌──────────────────────────┐
                 │        GitHub Repo       │
                 │  (source of truth code)  │
                 └─────────────┬────────────┘
                               │
                     Push commits / branches
                               │
                               ▼
        ┌──────────────────────────────────────────┐
        │              Supabase Platform            │
        │-------------------------------------------│
        │  • Auth                                  │
        │  • Database (Postgres)                   │
        │  • Storage                               │
        │  • Edge Functions (deployed from GitHub) │
        │  • Realtime                              │
        └───────────────┬──────────────────────────┘
                        │
                Auto‑deploy functions
                Sync branches → preview envs
                        │
                        ▼
           ┌──────────────────────────────┐
           │        React Frontend        │
           │ (calls Supabase APIs & funcs)│
           └───────────────┬─────────────┘
                           │
                 API calls / auth / queries
                           │
                           ▼
        ┌──────────────────────────────────────────┐
        │              Supabase Services            │
        │  • SQL queries to Postgres                │
        │  • Auth tokens validated                  │
        │  • Storage uploads/downloads              │
        │  • Edge Functions executed                │
        └──────────────────────────────────────────┘
