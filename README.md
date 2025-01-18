import pgzrun

HEIGHT = 345
WIDTH = 500

drone = Actor('drone')
drone.pos = 250,172.5

def draw():

    screen.blit("sky", (0,0))
    drone.draw()
    if drone.x == 0 and drone.y == 0:
        screen.draw.text(str("you have reached your destination"), (100,100), fontsize = 30)

def update():

    if keyboard.left:
        drone.x = drone.x - 2
        if drone.x <= 0:
            drone.x = 0
    
    elif keyboard.right:
        drone.x = drone.x + 2
        if drone.x >= 500:
            drone.x = 500
    
    elif keyboard.up:
        drone.y = drone.y - 2
        if drone.y <= 0:
            drone.y = 0
    
    elif keyboard.down:
        drone.y = drone.y + 2
        if drone.y >= 345:
            drone.y = 345


pgzrun.go()
