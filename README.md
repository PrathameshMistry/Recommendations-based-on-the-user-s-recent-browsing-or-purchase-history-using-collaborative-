Recommendations based on the user’s recent browsing or purchase history using collaborative

A sophisticated recommendation system that combines collaborative filtering and content-based approaches to provide personalized product recommendations based on user browsing and purchase history.
Features

Recommendations based on the user’s recent browsing or purchase history using collaborative Approach:
Combines both content-based and collaborative filtering methods
Real-time Processing: Uses Redis for caching recommendations to improve performance
Flexible Interaction Tracking: Supports multiple types of user interactions (views, cart additions, purchases)
Weighted Recommendations: Different weights for different types of user interactions
Automatic Cache Management: Smart cache invalidation when product features are updated
Scalable Architecture: Designed to handle large numbers of users and products

Requirements

Python 3.x
Redis Server
Required Python packages:

redis
pandas
scikit-learn
numpy



Installation

Clone the repository:

bashCopygit clone https://github.com/PrathameshMistry/Recommendations-based-on-the-user-s-recent-browsing-or-purchase-history-using-collaborative-

Install the required packages:

bashCopypip install redis pandas scikit-learn numpy

Install and start Redis server:

bashCopyapt-get install redis-server
redis-server --daemonize yes
Usage
Here's a basic example of how to use the recommendation system:
pythonCopyfrom recommendation_system import RecommendationSystem

# Initialize the system
recommender = RecommendationSystem()

# Add product information
recommender.add_product('P1', {
    'category': 'electronics',
    'brand': 'Apple',
    'price_range': 'high'
})

# Record user interactions
recommender.record_user_interaction('user1', 'P1', 'purchase')

# Get recommendations
recommendations = recommender.get_recommendations('user1', n=5)
print(recommendations)
How It Works
1. Content-Based Filtering

Analyzes product features using TF-IDF vectorization
Calculates similarity between products using cosine similarity
Recommends products similar to those the user has interacted with

2. Collaborative Filtering

Creates a user-product interaction matrix
Identifies similar users based on their interaction patterns
Recommends products that similar users have interacted with

3. Hybrid Approach

Combines recommendations from both approaches
Weights content-based recommendations at 60%
Weights collaborative recommendations at 40%
Caches final recommendations in Redis for improved performance

Performance Optimization

Uses Redis caching to store recommendations
Cache invalidation on product feature updates
Configurable cache TTL (default: 1 hour)
Efficient similarity calculations using scikit-learn

Configuration
The system can be configured by modifying the following parameters:

redis_host: Redis server host (default: 'localhost')
redis_port: Redis server port (default: 6379)
cache_ttl: Cache time-to-live in seconds (default: 3600)
Interaction weights:

View: 1.0
Add to cart: 2.0
Purchase: 3.0



Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
License
This project is licensed under the MIT License - see the LICENSE file for details.
Author
Prathamesh Mistry
Acknowledgments

Built using scikit-learn for efficient machine learning operations
Redis for high-performance caching
Pandas for data manipulation and analysis
