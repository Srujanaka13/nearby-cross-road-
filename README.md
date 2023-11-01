# nearby-cross-road-
import osmnx as ox

# User location or coordinates (latitude and longitude)
user_location = (37.7749, -122.4194)

# Download and process OpenStreetMap data for the area around the user
graph = ox.graph_from_point(user_location, distance=1000, network_type='all')

# Find the nearest nodes (crossroads)
nearest_nodes = ox.distance.nearest_nodes(graph, user_location)

# Retrieve the coordinates and other information for the nearest crossroads
crossroads = [(graph.nodes[node]['y'], graph.nodes[node]['x']) for node in nearest_nodes]

print("Nearby Crossroads:")
for i, crossroad in enumerate(crossroads):
    print(f"Crossroad {i+1}: Latitude {crossroad[0]}, Longitude {crossroad[1]}")
