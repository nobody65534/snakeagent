import pygame
import random
import numpy as np

# Initialize Pygame
pygame.init()

# Set up the game window
window_width, window_height = 800, 600
window = pygame.display.set_mode((window_width, window_height))
pygame.display.set_caption("Snake Game")

# Define colors
BLACK = (0, 0, 0)
GREEN = (0, 255, 0)
RED = (255, 0, 0)

# Define the snake and food sizes
snake_size = 20
food_size = 20

# Set the initial position of the snake
snake_x = window_width // 2
snake_y = window_height // 2

# Set the initial velocity of the snake
velocity_x = 0
velocity_y = 0

# Set the initial position of the food
food_x = random.randint(0, window_width - food_size) // 20 * 20
food_y = random.randint(0, window_height - food_size) // 20 * 20

# Initialize the snake's body
snake_body = []
snake_length = 1

# Set the game clock
clock = pygame.time.Clock()

# Define the game loop
running = True
while running:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP:
                velocity_x = 0
                velocity_y = -snake_size
            elif event.key == pygame.K_DOWN:
                velocity_x = 0
                velocity_y = snake_size
            elif event.key == pygame.K_LEFT:
                velocity_x = -snake_size
                velocity_y = 0
            elif event.key == pygame.K_RIGHT:
                velocity_x = snake_size
                velocity_y = 0

    # Move the snake
    snake_x += velocity_x
    snake_y += velocity_y

    # Check if the snake hits the boundary
    if snake_x < 0 or snake_x >= window_width or snake_y < 0 or snake_y >= window_height:
        running = False

    # Check if the snake eats the food
    if snake_x == food_x and snake_y == food_y:
        food_x = random.randint(0, window_width - food_size) // 20 * 20
        food_y = random.randint(0, window_height - food_size) // 20 * 20
        snake_length += 1
        print(f"{snake_length}" + "Long")
    # Update the snake's body
    snake_head = [snake_x, snake_y]
    snake_body.append(snake_head)
    if len(snake_body) > snake_length:
        del snake_body[0]

    # Check if the snake hits its own body
    if snake_head in snake_body[:-1]:
        running = False

    # Clear the game window
    window.fill(BLACK)

    # Draw the snake
    for segment in snake_body:
        pygame.draw.rect(window, GREEN, (segment[0], segment[1], snake_size, snake_size))

    # Draw the food
    pygame.draw.rect(window, RED, (food_x, food_y, food_size, food_size))

    # Update the game display
    pygame.display.update()

    # Set the game speed
    clock.tick(10)

# Quit the game
pygame.quit()
