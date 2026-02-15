# Sports Score Notification Service

## Overview

A Python-based implementation of the **Observer Design Pattern** for real-time sports score notifications. This service provides a pub-sub architecture to notify multiple subscribers about cricket and football match updates.

## Architecture

### Design Pattern: Observer (Pub-Sub)

The project implements the Observer design pattern with the following components:

#### Publishers
- **CricketPublisher** (Abstract Base Class)
  - `CricketScoreBoardPublisher` - Default cricket score publisher
  - `ESPNCricketScoreBoardPublisher` - ESPN cricket score source
  - `SonyCricketScoreBoardPublisher` - Sony cricket score source
  
- **FootBallPublisher** (Abstract Base Class)
  - `FootBallScorePublisher` - Football score publisher

#### Subscribers
- **CricketSubscriber** (Abstract Interface)
  - `PredictedScoreSubscriber` - Predicts final scores based on current data
  - `RunRateSubscriber` - Calculates and tracks run rates
  - `TopDiscussionSubscriber` - Manages top discussion topics

- **FootBallSubscriber** (Abstract Interface)
  - Implemented by `PredictedScoreSubscriber` for multi-sport support

## Core Features

### Cricket Score Updates
- **Runs**: Current runs scored
- **Wickets**: Number of wickets fallen
- **Over**: Current over number (e.g., 20.1)

### Football Score Updates
- **Goal1**: Goals by team 1
- **Goal2**: Goals by team 2
- **Duration**: Match duration in minutes

### Subscriber Capabilities
- Subscribe to publisher updates
- Unsubscribe from publishers
- Persist details in database
- Calculate projected scores
- Update board displays

## Project Structure
sports-score-notification-service/
├── publisher/
│ ├── cricket_publisher.py
│ ├── cricket_score_board_publisher.py
│ ├── espn_cricket_score_board_publisher.py
│ ├── sony_cricket_score_board_publisher.py
│ └── foot_ball_score_publisher.py
├── subscriber/
│ ├── cricket_subscriber.py
│ ├── foot_ball_subscriber.py
│ ├── predicted_score_subscriber.py
│ ├── run_rate_subscriber.py
│ └── top_discussion_subscriber.py
├── tester/
│ ├── pub_sub_tester.py
│ └── __init__.py
└── README.md


## Usage Example

```python
from tester.pub_sub_tester import PubSubTester

# Run the pub-sub test
PubSubTester.test()

PredictedScoreSubscriber: runs = 100 wickets = 2 over = 20.1
RunRateSubscriber: runs = 100 wickets = 2 over = 20.1
TopDiscussionSubscriber: runs = 100 wickets = 2 over = 20.1
PredictedScoreSubscriber: runs = 110 wickets = 3 over = 21.1
RunRateSubscriber: runs = 110 wickets = 3 over = 21.1

