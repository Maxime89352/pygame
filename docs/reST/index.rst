import pygame
import sys

# Initialiser Pygame
pygame.init()

# Définir les dimensions de la fenêtre
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))

# Charger l'image du personnage (assurez-vous d'avoir une image de personnage)
character_image = pygame.image.load('character.png')
character_rect = character_image.get_rect()

# Définir la position initiale du personnage
character_rect.topleft = (screen_width // 2, screen_height // 2)

# Vitesse de déplacement du personnage
character_speed = 5

# Boucle principale du jeu
while True:
    # Gestion des événements
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Gérer les touches appuyées
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        character_rect.x -= character_speed
    if keys[pygame.K_RIGHT]:
        character_rect.x += character_speed
    if keys[pygame.K_UP]:
        character_rect.y -= character_speed
    if keys[pygame.K_DOWN]:
        character_rect.y += character_speed

    # Remplir l'écran de noir
    screen.fill((0, 0, 0))

    # Dessiner le personnage
    screen.blit(character_image, character_rect)

    # Mettre à jour l'affichage
    pygame.display.flip()

    # Contrôler la vitesse de l'animation
    pygame.time.Clock().tick(60)
