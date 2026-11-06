# Playbooks

## zjleblanc.tmdb.tmdb_collection

List favorite movies, add Dune (`438631`), then remove it.

### Variables

| Name | Required | Default | Description | Example |
| --- | --- | --- | --- | --- |
| tmdb_api_url | no | `{{ lookup('ansible.builtin.env', 'TMDB_API') }}` | Base URL passed to each module. `TMDB_API` must be set. | `https://api.themoviedb.org/3` |
| tmdb_api_key | no | `{{ lookup('ansible.builtin.env', 'TMDB_API_KEY') }}` | API key passed to each module. `TMDB_API_KEY` must be set. | `{{ lookup('ansible.builtin.env', 'TMDB_API_KEY') }}` |
| tmdb_username | no | `{{ lookup('ansible.builtin.env', 'TMDB_USERNAME') }}` | Account username passed to each module. `TMDB_USERNAME` must be set. | `{{ lookup('ansible.builtin.env', 'TMDB_USERNAME') }}` |
| tmdb_password | no | `{{ lookup('ansible.builtin.env', 'TMDB_PASSWORD') }}` | Account password passed to each module. `TMDB_PASSWORD` must be set. | `{{ lookup('ansible.builtin.env', 'TMDB_PASSWORD') }}` |
| account_id | yes | `20850360` | TMDB account id set on each task. | `20850360` |
| movie_id | yes | `438631` | Movie added, then removed. Dune (2021). | `438631` |

### Example

```bash
export TMDB_API=https://api.themoviedb.org/3
export TMDB_API_KEY="<your-tmdb-api-key>"
export TMDB_USERNAME="<your-tmdb-username>"
export TMDB_PASSWORD="<your-tmdb-password>"
ansible-playbook zjleblanc.tmdb.tmdb_collection
```

## zjleblanc.tmdb.tmdb_uri

Authenticate to TMDB with `ansible.builtin.uri` and list favorite movies.

### Variables

| Name | Required | Default | Description | Example |
| --- | --- | --- | --- | --- |
| tmdb_api_url | no | `https://api.themoviedb.org/3` | Base URL for the TMDB API. | `https://api.themoviedb.org/3` |
| tmdb_account_id | no | `20850360` | Account whose favorite movies are listed. | `20850360` |
| tmdb_api_key | no | `{{ lookup('env', 'TMDB_API_KEY') }}` | API key. The default reads `TMDB_API_KEY`, which must be set. | `{{ lookup('ansible.builtin.env', 'TMDB_API_KEY') }}` |
| tmdb_username | no | `{{ lookup('env', 'TMDB_USERNAME') }}` | Account username. The default reads `TMDB_USERNAME`, which must be set. | `{{ lookup('ansible.builtin.env', 'TMDB_USERNAME') }}` |
| tmdb_password | no | `{{ lookup('env', 'TMDB_PASSWORD') }}` | Account password. The default reads `TMDB_PASSWORD`, which must be set. | `{{ lookup('ansible.builtin.env', 'TMDB_PASSWORD') }}` |

### Example

```bash
export TMDB_API_KEY="<your-tmdb-api-key>"
export TMDB_USERNAME="<your-tmdb-username>"
export TMDB_PASSWORD="<your-tmdb-password>"
ansible-playbook zjleblanc.tmdb.tmdb_uri -e tmdb_account_id=20850360
```
