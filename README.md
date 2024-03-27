- 👋 Hi, I’m @LRivera12
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...


<!---
LRivera12/LRivera12 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up the screen
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Car Racing Game")

# Set up colors
white = (255, 255, 255)
black = (0, 0, 0)

# Set up the car
car_image = pygame.image.load("car.png")
car_rect = car_image.get_rect()
car_rect.center = (screen_width // 2, screen_height // 2)

# Set up movement variables
speed = 5
angle = 0

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Handle user input
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        angle += 5
    if keys[pygame.K_RIGHT]:
        angle -= 5

    # Move the car
    car_rect = car_rect.move(speed * pygame.math.cos(pygame.math.radians(angle)),
                             -speed * pygame.math.sin(pygame.math.radians(angle)))

    # Draw everything
    screen.fill(white)
    rotated_car = pygame.transform.rotate(car_image, angle)
    rotated_rect = rotated_car.get_rect(center=car_rect.center)
    screen.blit(rotated_car, rotated_rect)
    pygame.display.flip()

    # Cap the frame rate
    pygame.time.Clock().tick(60)

# Quit Pygame
pygame.quit()
sys.exit()
