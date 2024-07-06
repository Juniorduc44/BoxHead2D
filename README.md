# BoxHead2D

[![Video](https://img.youtube.com/vi/Y7BeCjsXLb8/maxresdefault.jpg)](https://www.youtube.com/embed/Y7BeCjsXLb8)

A simple BoxHead Survivor game in 2D with [Python Arcade](https://api.arcade.academy/en/latest/index.html). 

This is a "rogue-lite", "top-down shooter" game. The core gameplay is a combination of an old 3D BoxHead zombie game and a recent popular survivor-style game.

Requirements for running in the terminal:

- Python 3.6+
- Arcade library(Windows) `pip install arcade` or `pip install -r requirements.txt`
- Arcade library(Linux) `pip3 install arcade` or `pip3 install -r requirements.txt`

Run the game with the command:
```python
python app.py # Windows environment
python3 app.py # Linux or Mac
```

### Design Document

#### Player

| Characters | Health | Energy | Money | Speed | Kill recover | Explosion Damage | Luck |
|------------|--------|--------|-------|-------|--------------|------------------|------|
| Player     |    100 |      0 |     0 |  1600 |            5 |              100 |    6 |

#### Weapons

| Weapons    | Damage           | Energy cost | CD | Attack range (bullet life span) | Bullet speed | Bullet number | Health |
|------------|------------------|-------------|----|---------------------------------|--------------|---------------|--------|
| Pistol     |               30 |           0 | 30 |                              20 |           25 | \             | \      |
| Uzi        |               30 |           3 | 20 |                              25 |           30 | \             | \      |
| Shotgun    | 40*3             |          12 | 50 |                              10 |           25 |             3 | \      |
| Rocket     | explosion damage |          20 | 40 |                              15 |           32 |             1 | \      |
| PlacedWall | \                |           5 |  4 |                                 | \            | \             |    300 |
| Barrel     | explosion damage |          20 |  4 |                                 | \            | \             |      0 |
| Mine       | explosion damage |          20 |  4 |                                 | \            | \             |      0 |

#### Enemies

| Enemies   | Health | Hit Damage | Bullet damage | Speed | CD  | Attack range | Bullet speed |
|-----------|--------|------------|---------------|-------|-----|--------------|--------------|
| White     |    100 |         20 | \             |   800 | \   | \            | \            |
| Red       |    300 |         20 |            30 |   800 | 120 |          200 |            6 |
| Crack     |    200 |         40 | \             |  1000 | \   | \            | \            |
| Big Mouth |    150 |         20 | 50*2          |   800 |  70 |          300 |            7 |
| Crash     |    100 |         80 | \             |  1000 | \   |          200 | \            |
| Tank      |    400 |        120 | \             |   800 | \   |          200 | \            |

#### Items

Quality:

- Bronze: base value
- Sliver: 2 * base value
- Gold: 4 * base value

| Items                        | Base quality | Base value | Base cost |
|------------------------------|--------------|------------|-----------|
| Sell health                  |            1 |        100 |       -18 |
| Sell energy                  |            1 |         50 |       -12 |
| Add speed                    |            1 |         50 |        15 |
| Sell speed                   |            1 |         50 |       -15 |
| Increase luck                |            1 |          2 |        18 |
| Sell luck                    |            1 |          2 |       -18 |
| Add kill recover             |            1 |          5 |        12 |
| Increase explosion damage    |            1 |         50 |        30 |
| Increase pistol damage       |            1 |         10 |         9 |
| Reduce pistol CD             |            1 |          2 |        14 |
| Increase pistol attack range |            1 |          5 |        16 |
| Add Uzi                      |           -1 | \          |        30 |
| Add Shotgun                  |           -1 | \          |        42 |
| Add Rocket                   |           -1 | \          |        56 |
| Add Wall                     |           -1 | \          |        28 |
| Add Barrel                   |           -1 | \          |        52 |
| Add MIne                     |           -1 | \          |        49 |
|                              |              |            |           |
| Uzi                          |              |            |           |
| Add Uzi damage               |            1 |         10 |        21 |
| Reduce Uzi CD                |            1 |          2 |        19 |
| Add Uzi range                |            1 |          5 |        20 |
| Reduce Uzi cost              |            1 |          1 |        18 |
| Sell Uzi                     |           -1 | \          |       -30 |
|                              |              |            |           |
| Shotgun                      |              |            |           |
| Add Shotgun damage           |            1 |         10 |        36 |
| Reduce Shotgun CD            |            1 |          3 |        21 |
| Add Shotgun range            |            1 |          5 |        28 |
| Reduce Shotgun cost          |            1 |          1 |        24 |
| Sell Shotgun                 |           -1 | \          |       -42 |
| Add Shotgun bullets          |            1 |          1 |        26 |
|                              |              |            |           |
| Rocket                       |              |            |           |
| Reduce Rocket CD             |            1 |          2 |        19 |
| Add Rocket range             |            1 |          5 |        20 |
| Reduce Rocket cost           |            1 |          1 |        18 |
| Sell Rocket                  |           -1 | \          |       -30 |
|                              |              |            |           |
| Wall                         |              |            |           |
| Add Wall health              |            1 |         20 |        24 |
| Sell Wall                    |           -1 | \          |           |
| Reduce Wall cost             |            1 |          1 |        16 |
|                              |              |            |           |
| Barrel                       |              |            |           |
| Sell Barrel                  |           -1 | \          |       -52 |
| Reduce Barrel cost           |            1 |          1 |        35 |
|                              |              |            |           |
| Mine                         |              |            |           |
| Sell Mine                    |           -1 | \          |       -49 |
| Reduce Mine cost             |            1 |          1 |        28 |
|                              |              |            |           |
| Rocket multi explosion       |           -1 | \          |        52 |
| Barrel multi explosion       |           -1 | \          |        45 |
| Mine multi explosion         |           -1 | \          |        48 |

#### Round

Item actual price = Round * Base Pirce *2

Total number of enemy = Round * 8

### Credits

This project uses the following free resources:

- [Electronic Rock (King Around Here) | Royalty-free Music - Pixabay](https://pixabay.com/music/beats-electronic-rock-king-around-here-15045/)
- [Free Music | Download Royalty Free Music | Zapsplat](https://www.zapsplat.com/sound-effect-category/royalty-free-music/)
- [ACh-K/Cubic-11: 免費開源的 11×11 中文點陣體 (github.com)](https://github.com/ACh-K/Cubic-11)
- [Snake's Authentic Gun Sounds by SnakeF8 (itch.io)](https://f8studios.itch.io/snakes-authentic-gun-sounds)
