#!/bin/bash

# Function to prompt user for their guess
function guess_files {
    local file_count=$(ls -1 | wc -l)
    local guess=0

    echo "Welcome to the Guessing Game!"
    echo "How many files are in the current directory?"

    while [[ $guess -ne $file_count ]]; do
        read -p "Enter your guess: " guess

        if [[ $guess -lt $file_count ]]; then
            echo "Your guess is too low. Try again."
        elif [[ $guess -gt $file_count ]]; then
            echo "Your guess is too high. Try again."
        else
            echo "Congratulations! You guessed it right!"
        fi
    done
}

# Call the function
guess_files
# Makefile to generate README.md

README.md: guessinggame.sh
	@echo "# Guessing Game" > README.md
	@echo "Date and Time: $(shell date)" >> README.md
	@echo "Number of lines of code: $(shell wc -l < guessinggame.sh)" >> README.md

clean:
	rm -f README.md
your_project_directory/
├── guessinggame.sh
├── Makefile
└── README.md (will be generated)
chmod +x guessinggame.sh
make
bash guessinggame.sh
