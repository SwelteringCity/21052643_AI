# 21052643_AI
# AI Assignment Report
Github repo
Assignment 2  
Roll number: 21052643


After the canvas creation and random population generation, the following steps are performed in a loop a specified number of times or until a decent enough image is generated.

## Implementation of cross-over
The crossover method is one point, here a random point along the chromosome is selected. The portion of the chromosome before the point is copied from one parent, and the portion after the point is copied from another parent to create the offspring.
In a canvas-based representation, each image can be composed of several elements, such as squares, circles, or other shapes. Each element is defined by its position, size, color, and other attributes on the canvas.To perform crossover on this canvas, we create a custom crossover method that combines elements from two parent images to produce offspring.

The following algorithm is used to perform the cross-over when a canvas based approach is used:
Function CustomCrossover(parent1, parent2):
    # Create empty canvases for the offspring
    offspring1 = CreateEmptyCanvas()
    offspring2 = CreateEmptyCanvas()

    # Randomly select a crossover point along the canvas
    crossover_point = RandomPosition()

    # Copy elements from parent1 to offspring1 up to the crossover point
    CopyElements(parent1, offspring1, up_to=crossover_point)
    
    # Copy elements from parent2 to offspring2 from the crossover point
    CopyElements(parent2, offspring2, from_position=crossover_point)
    
    Return offspring1, offspring2


## Implementation of mutation
The mutation is implemented by making random changes to the values of 	the pixels. In case of the canvas based representation of the image, the changes are made to the canvas. Here, we use numpy to make an array of the image where it is represented in RGB format. 

The following algorithm serves as the skeleton for the mutation implementation in this assignment.

Function PixelMutation(image, mutation_rate):
    # Create a copy of the original image
    mutated_image = CopyImage(image)
    
    # Determine the number of pixels to mutate based on the mutation rate
    num_pixels_to_mutate = mutation_rate * TotalNumberOfPixels(image)
    
    for i from 1 to num_pixels_to_mutate:
        # Select a random pixel position
        pixel_x, pixel_y = RandomPixelPosition(image)
        
        # Generate a random value to replace the pixel value
        new_pixel_value = RandomPixelValue()
        
        # Mutate the pixel in the mutated image
        SetPixelValue(mutated_image, pixel_x, pixel_y, new_pixel_value)
    
    Return mutated_image



## Implementation of selection
The population with the highest fitness score is selected using the roulette wheel method. The objective is to emphasize the quality of the generated images and ensure that better solutions have a higher chance of being passed on to the next generation, fitness proportionate selection is a suitable choice. It rewards high-quality solutions with higher probabilities of being selected.

The following algorithm is used as a base case:

Function RouletteWheelSelection(population, fitness_values):
    total_fitness = sum(fitness_values)
    random_value = RandomFloat(0, total_fitness)  # Generate a random value in [0, total_fitness)
    
    cumulative_fitness = 0
    selected_index = 0
    
    for i from 0 to (population_size - 1):
        cumulative_fitness += fitness_values[i]
        if cumulative_fitness >= random_value:
            selected_index = i
            break
    
    selected_individual = population[selected_index]
    return selected_individual





