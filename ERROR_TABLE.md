# Error table

One row per failure. Fill in every column. You need at least eight rows.

| Scenario | Function that detects it | Error value | What the player sees |
|---|---|---|---|
| Fleet file does not exist | `load_fleet` | `Err(DataError::Io(..))` (kind `NotFound`) | _(example: your row goes here)_ |
| Fleet path is a directory (`data`) | `load_fleet` | `Err(DataError::Io(..))` | `Error: could not load data: Is a directory` |  |  |  |  |
| Fleet file contains only comments | `load_fleet` | `Err(DataError::NoShips(path))` | `Error: could not load data/fleet_empty.txt: no valid ships in data/fleet_empty.txt` |
| Fleet file contains only invalid ship lines | `load_fleet` | `Err(DataError::NoShips(path))` | `Error: could not load data/fleet_all_bad.txt: no valid ships in data/fleet_all_bad.txt` |  |  |  |  |
| Board file has 9 rows | `parse_board` | `BoardError::WrongRowCount(9)` | `Practice board unavailable: bad board layout: board has 9 rows instead of 10` | |  |  |  |
| Board file contains an invalid character (`x`) | `parse_board` | `BoardError::BadChar { line: 6, ch: 'x' }` | `Practice board unavailable: bad board layout: line 6 contains invalid character 'x'` |  |  |  |  |
| Scores file does not exist | `load_scores` | `Ok(Vec::new())` | `no scores yet` |
| Scores path is a directory (`data`) | `load_scores` | `Err(DataError::Io(..))` | `scores unavailable: Is a directory` |  |  |  |  |
| Saving a score fails | `append_score` | `Err(DataError::Io(..))` | `Could not save the score: <message>` | |  |  |  |
| User enters `K11` | `parse_coord` | `Err(CoordError::ColumnOutOfRange('K'))` | `column K is off the board (A-J)` |

Scenarios to cover (add more if you find them):

- fleet file missing
- a directory given as the fleet path
- fleet file with only comments
- fleet file where every line is bad
- board file with nine rows
- board file with a bad character
- scores file missing
- scores file that cannot be written
- `K11` typed at the prompt


