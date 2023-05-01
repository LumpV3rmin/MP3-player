# MP3-player
import tkinter as tk

import pygame

# Initialize Pygame mixer
pygame.init()
pygame.mixer.init()

# Define the path to the music file
music_path = "C:/Users/LumpV3rmin/Music/Playlists"


# Define a function to play the music
def play_music():
    try:
        # Load the music file
        pygame.mixer.music.load("path/to/music/file")
        # Play the music
        pygame.mixer.music.play()
    except pygame.error as e:
        print("Error playing music:", e)


def pause_music():
    pygame.mixer.music.pause()


def stop_music():
    pygame.mixer.music.stop()


def skip_music():
    # Load the next music file in the playlist and play it
    pass  # add your own code here


# Create the main window
root = tk.Tk()

# Add a button to play the music
play_button = tk.Button(root, text="Play", command=play_music)
play_button.pack()
pause_button = tk.Button(root, text="Pause", command=pause_music)
pause_button.pack()
stop_button = tk.Button(root, text="Stop", command=stop_music)
stop_button.pack()
skip_button = tk.Button(root, text="Skip", command=skip_music)
skip_button.pack()

# Slider for volume control
volume_slider = tk.Scale(root, from_=0, to=100, orient=tk.HORIZONTAL)

# Set the initial volume
pygame.mixer.music.set_volume(0.5)


# Volume control to the slider
def set_volume(val):
    volume = int(val) / 100
    pygame.mixer.music.set_volume(volume)


volume_slider.config(command=set_volume)

# Run the program
root.mainloop()
