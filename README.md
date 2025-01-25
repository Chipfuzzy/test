import pgzrun

HEIGHT = 345
WIDTH = 500
TARGET_COORDINATE = (0,0) 
TIME_LIMIT = 20  

drone = Actor('drone')
drone.pos = 250,172.5
remaining_time = TIME_LIMIT
game_over = False
message = ""

def update():
    global remaining_time, game_over, message

    if not game_over:
       
        remaining_time -= 1 / 60 

        if drone.pos == TARGET_COORDINATE:
            game_over = True
            message = "You reached the target in time! You win!"

        if remaining_time <= 0:
            game_over = True
            remaining_time = 0
            message = "Time's up! You lose."


def draw():

    screen.blit("sky", (0,0))
    drone.draw()
    screen.draw.filled_circle(TARGET_COORDINATE, 5, "red")

    screen.draw.text(f"Time: {remaining_time:.1f} seconds", (10, 10), color="white", fontsize=30)

    if game_over:
        screen.draw.text(message, (WIDTH // 2 - 200, HEIGHT // 2), color="yellow", fontsize=30)

    
def on_key_down(key):
    if not game_over:

        if keyboard.left:
            drone.x = drone.x - 20
            if drone.x <= 0:
                drone.x = 0
    
        elif keyboard.right:
            drone.x = drone.x + 20
            if drone.x >= 500:
                drone.x = 500
    
        elif keyboard.up:
            drone.y = drone.y - 20
            if drone.y <= 0:
                drone.y = 0
    
        elif keyboard.down:
            drone.y = drone.y + 20
            if drone.y >= 345:
                drone.y = 345

pgzrun.go()
