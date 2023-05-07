-- write your queries here
video_games_tb = "CREATE TABLE video_games(
    id INT PRIMARY KEY,
    name VARCHAR(150) NOT NULL,
    game_genre VARCHAR(150),
    game_developer VARCHAR(150) NOT NULL,
    release_date DATE
);"

game_developers_tb = "CREATE TABLE game_developers(
    id INT PRIMARY KEY,
    name VARCHAR(150),
    address VARCHAR(150),
    state VARCHAR(150),
    city VARCHAR(150) NOT NULL,
    country VARCHAR(150) NOT NULL
);
"

platforms_tb = "CREATE TABLE platforms(
    id INT PRIMARY KEY,
    name VARCHAR(150),
    company_id INT,
    company VARCHAR(150),
    release_date DATE,
    original_price REAL NOT NULL
);"

platforms_games_tb = "CREATE TABLE platforms_games(
    game_id INT,
    platform_id INT,
    platform_name VARCHAR(150),
    PRIMARY KEY (game_id, platform_id),
    CONSTRAINT fk_video_games FOREIGN KEY (game_id)
    REFERENCES video_games(id),
    CONSTRAINT fk_platforms FOREIGN KEY (platform_id)
    REFERENCES platforms(id)
);"

characters_tb = "CREATE TABLE characters(
    id INT PRIMARY KEY,
    name VARCHAR(150),
    birthday DATE,
    gender REAL,
    info VARCHAR(300)
);"

games_characters_tb = "CREATE TABLE games_characters(
    character_id INT,
    game_id INT,
    character_name VARCHAR(150),
    PRIMARY KEY(character_id, game_id),
    CONSTRAINT fk_characters FOREIGN KEY (character_id)
    REFERENCES characters(id),
    CONSTRAINT fk_video_games FOREIGN KEY(game_id)
    REFERENCES video_games(id)
);"


