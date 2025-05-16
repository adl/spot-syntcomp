Build this docker image with

```sh
docker build -t spot-syntcomp25 .
```

To run ltlsynt/ltlfsynt against `spec.tlsf` in the local directory, execute:

```sh
docker run -v .:/LOCAL:ro spot-syntcomp25 CONFIG /LOCAL/spec.tlsf
```

where `CONFIG` should be one of the following:

| `CONFIG`               | Description                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------|
| `ltlfsynt-real-dfs-os` | LTLf realizability with DFS exploration and one-step (un)realizability checks                   |
| `ltlfsynt-real-dfs`    | LTLf realizability with DFS exploration, without one-step (un)realizability checks              |
| `ltlfsynt-real-bfs-os` | LTLf realizability with DFS exploration and one-step (un)realizability checks                   |
|------------------------|-------------------------------------------------------------------------------------------------|
| `ltlsynt-real-acd`     | LTL realizability, with translation to parity game based on ACD transform of deterministic TELA |
| `ltlsynt-real-lar`     | LTL realizability, with translation to parity game based on LAR transform of deterministic TELA |
| `ltlsynt-real-ds`      | LTL realizability, with translation to parity game based on determinization of NBA              |
|------------------------|-------------------------------------------------------------------------------------------------|
| `ltlsynt-syn-acd`      | LTL synthesis, with translation to parity game based on ACD transform of deterministic TELA     |
| `ltlsynt-syn-lar`      | LTL synthesis, with translation to parity game based on LAR transform of deterministic TELA     |
| `ltlsynt-syn-ds`       | LTL synthesis, with translation to parity game based on determinization of NBA                  |



