# Go tournament generator
Go package to generate tournaments automatically.

## How to use

The next code snippet shows how to create a `double-round` competition.

```go
package main

// Import tournament generator
import (
  generator "github.com/nunovieira220/tournament-generator-go"
)

// List of all teams
teams := []string{"Team1", "Team2", "Team3", "Team4"};
options := map[string]string{Type: "double-round"};

// Generate and get games
games, error := generator.Generate(teams, options);
```

The next JSON snippet shows the possible content of the `games` entity.

```json
[
  { "awayTeam": "Team1", "homeTeam": "Team3", "round": 1 },
  { "awayTeam": "Team4", "homeTeam": "Team2", "round": 1 },
  { "awayTeam": "Team2", "homeTeam": "Team1", "round": 2 },
  { "awayTeam": "Team3", "homeTeam": "Team4", "round": 2 },
  { "awayTeam": "Team1", "homeTeam": "Team4", "round": 3 },
  { "awayTeam": "Team3", "homeTeam": "Team2", "round": 3 },
  { "awayTeam": "Team3", "homeTeam": "Team1", "round": 4 },
  { "awayTeam": "Team2", "homeTeam": "Team4", "round": 4 },
  { "awayTeam": "Team1", "homeTeam": "Team2", "round": 5 },
  { "awayTeam": "Team4", "homeTeam": "Team3", "round": 5 },
  { "awayTeam": "Team4", "homeTeam": "Team1", "round": 6 },
  { "awayTeam": "Team2", "homeTeam": "Team3", "round": 6 }
]
```

### Properties

At the moment the only supported property is the type and there are three possible tournament types to generate:

- `double-round`: A championship competition where teams play against each other twice, one at home and one away.

- `single-round`: A championship competition where teams play against each other one single time.

- `simple-cup`: A cup competition that basically generates the first round (or the first two rounds) randomly.

You can see a better description of the competition types [here](docs/competition-type.md).

## Test

To run the package tests, you just need to execute:

```sh
go test -v ./tests
```
