# video-cstp-big
convert super stop big
# Code for Batch Video Conversion using moviepy
from moviepy.editor import VideoFileClip
import os

def convert_folder_to_mp4(input_folder, output_folder):
    # Check if output folder exists, create it if not
    if not os.path.exists(output_folder):
        os.makedirs(output_folder)

    # Get a list of all files in the input folder
    files = os.listdir(input_folder)

    # Iterate through each file in the folder
    for file in files:
        # Check if the file is a supported video file
        if file.lower().endswith(('.avi', '.mp4', '.mkv')):
            # Build the full file paths
            input_file_path = os.path.join(input_folder, file)
            output_file_path = os.path.join(output_folder, os.path.splitext(file)[0] + ".mp4")

            # Load the video clip
            video_clip = VideoFileClip(input_file_path)

            # Export as MP4
            video_clip.write_videofile(output_file_path, codec='libx264', audio_codec='aac', preset='ultrafast')

            print(f"Conversion complete for {file}. MP4 file saved at {output_file_path}")

# Example usage
input_folder_path = "path/to/your/input/folder"
output_folder_path = "path/to/your/output/folder"

convert_folder_to_mp4(input_folder_path, output_folder_path)
