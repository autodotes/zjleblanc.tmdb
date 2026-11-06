# Ansible Collection - zjleblanc.tmdb

The Movie Database (TMDB) automation content.

[Galaxy](https://galaxy.ansible.com/ui/repo/published/zjleblanc/tmdb/) | [Changelog](CHANGELOG.md)

## Requirements

- Ansible `>=2.15.0`
- A TMDB API key and account credentials, passed as module options or through `TMDB_API`, `TMDB_API_KEY`, `TMDB_USERNAME`, `TMDB_PASSWORD`, and `TMDB_ACCOUNT_ID`

## Contents

### Playbooks

| Name | Description |
| --- | --- |
| [tmdb_collection](playbooks/tmdb_collection.yml) | List, add, and remove a favorite movie. |
| [tmdb_uri](playbooks/tmdb_uri.yml) | Authenticate to TMDB with the URI module and list favorite movies. |

Variables and run examples are in [playbooks/README.md](playbooks/README.md).

### Modules

| Name | Description |
| --- | --- |
| [favorite_movies](plugins/modules/favorite_movies.py) | Update favorite movies for a TMDB account |
| [favorite_movies_info](plugins/modules/favorite_movies_info.py) | Retrieve favorite movies for a TMDB account |

#### favorite_movies

```yaml
- name: Add a favorite movie
  zjleblanc.tmdb.favorite_movies:
    api_url: https://api.themoviedb.org/3
    api_key: "{{ lookup('ansible.builtin.env', 'TMDB_API_KEY') }}"
    username: "{{ lookup('ansible.builtin.env', 'TMDB_USERNAME') }}"
    password: "{{ lookup('ansible.builtin.env', 'TMDB_PASSWORD') }}"
    account_id: "12345"
    movie_id: "438631"

- name: Remove a favorite movie
  zjleblanc.tmdb.favorite_movies:
    api_url: https://api.themoviedb.org/3
    api_key: "{{ lookup('ansible.builtin.env', 'TMDB_API_KEY') }}"
    username: "{{ lookup('ansible.builtin.env', 'TMDB_USERNAME') }}"
    password: "{{ lookup('ansible.builtin.env', 'TMDB_PASSWORD') }}"
    account_id: "12345"
    movie_id: "438631"
    state: absent
```

#### favorite_movies_info

```yaml
- name: Get favorite movies
  zjleblanc.tmdb.favorite_movies_info:
    api_url: https://api.themoviedb.org/3
    api_key: "{{ lookup('ansible.builtin.env', 'TMDB_API_KEY') }}"
    username: "{{ lookup('ansible.builtin.env', 'TMDB_USERNAME') }}"
    password: "{{ lookup('ansible.builtin.env', 'TMDB_PASSWORD') }}"
    account_id: "12345"
```

## Installation

```bash
ansible-galaxy collection install zjleblanc.tmdb
```

## License

GNU General Public License v3.0 or later. See [LICENSE](LICENSE).
