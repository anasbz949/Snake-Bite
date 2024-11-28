![Screenshot (33)](https://github.com/user-attachments/assets/2aa17603-430a-4c11-ac95-a7263662ec60)

This Game's every single function's detailed explaination  

 **Global Variables**
1. **`static bool allowMove = false;`**
   - Declares a static boolean variable `allowMove`, initialized to `false`.
   - Used to ensure that the snake moves only after a certain interval or condition is met.

2. **`Color green = {173, 204, 96, 255};`**
   - Defines the `green` color with RGBA values (Red, Green, Blue, Alpha).
   - This will be used as the background color of the game.

3. **`Color darkGreen = {43, 51, 24, 255};`**
   - Similar to `green`, this is another color, used for snake and other graphical elements.

4. **`int cellSize = 30;`**
   - Defines the size of a single cell in the grid in pixels.

5. **`int cellCount = 25;`**
   - Defines the total number of cells in a row or column of the grid.

6. **`int offset = 75;`**
   - Sets a margin around the grid to provide spacing for the UI elements.

7. **`double lastUpdateTime = 0;`**
   - Tracks the time of the last update to control the game's timing and ensure smooth animation.


 **Helper Functions**
8. **`bool ElementInDeque(Vector2 element, deque<Vector2> deque)`**
   - Checks if a specific `Vector2` (x, y coordinate) exists in a deque (a double-ended queue).
   - Loops through each element of the deque. If `element` matches any, it returns `true`.
   - If no match is found, it returns `false`.

9. **`bool EventTriggered(double interval)`**
   - Determines if a specific time interval has passed.
   - Uses the difference between the current time (`GetTime()`) and `lastUpdateTime` to calculate this.
   - If the interval has passed, updates `lastUpdateTime` and returns `true`; otherwise, `false`.


**Class: Snake**
10. **`deque<Vector2> body = {...};`**
    - Represents the snake's body as a deque of `Vector2` positions. 
    - Starts with three segments at specific positions.

11. **`Vector2 direction = {1, 0};`**
    - The snake's movement direction. Initially set to move right.

12. **`bool addSegment = false;`**
    - A flag to determine if the snake should grow by adding a segment.

13. **`void Draw()`**
    - Loops through each segment of the snake's body.
    - Calculates the segment's position on the screen and draws it using `DrawRectangleRounded`.

14. **`void Update()`**
    - Updates the snake's position by adding a new head (based on `direction`) and optionally removing the tail.
    - If `addSegment` is `true`, the tail is not removed, making the snake grow.

15. **`void Reset()`**
    - Resets the snake to its initial size and position.


**Class: Food**
16. **`Food(deque<Vector2> snakeBody)`**
    - Constructor: Initializes the `Food` object.
    - Loads the food texture from an image and sets its initial position to a random valid cell.

17. **`~Food()`**
    - Destructor: Frees the memory used by the texture.

18. **`void Draw()`**
    - Draws the food at its position on the screen using the loaded texture.

19. **`Vector2 GenerateRandomCell()`**
    - Generates a random cell position within the grid.

20. **`Vector2 GenerateRandomPos(deque<Vector2> snakeBody)`**
    - Generates a random position for food that is not on the snake's body.
    - Uses `ElementInDeque` to ensure no overlap.


 **Class: Game**
21. **`Snake snake = Snake();`**
    - Initializes the `snake` object.

22. **`Food food = Food(snake.body);`**
    - Initializes the `food` object, ensuring the food is placed away from the snake.

23. **`bool running = true;`**
    - A flag to indicate if the game is running.

24. **`int score = 0;`**
    - Tracks the player's score.

25. **`Sound eatSound, wallSound;`**
    - Stores the sound effects for eating food and hitting walls.

26. **`Game()`**
    - Constructor: Initializes audio and loads sound effects.

27. **`~Game()`**
    - Destructor: Frees sound resources and closes the audio device.

28. **`void Draw()`**
    - Draws the game elements: food and snake.

29. **`void Update()`**
    - Updates the game state: moves the snake and checks collisions.

30. **`void CheckCollisionWithFood()`**
    - Checks if the snake's head has eaten the food. If so:
        - Generates new food.
        - Grows the snake.
        - Increases the score.
        - Plays a sound.

31. **`void CheckCollisionWithEdges()`**
    - Checks if the snake hits the grid boundaries. If so, triggers `GameOver()`.

32. **`void CheckCollisionWithTail()`**
    - Checks if the snake collides with itself. If so, triggers `GameOver()`.

33. **`void GameOver()`**
    - Resets the game and plays a sound.


 **Main Function**
34. `InitWindow(...);`
    - Initializes the game window with a specific size and title.

35. `SetTargetFPS(60);`
    - Sets the frame rate to 60 FPS for smooth gameplay.

36. `Game game = Game();`
    - Creates the `Game` object.

37. Game Loop: `while (WindowShouldClose() == false)`
    - The main loop continues until the window is closed.
    - Handles:
        - Movement input (`IsKeyPressed`).
        - Updates (`game.Update`).
        - Rendering (`game.Draw`).

38. `EventTriggered(0.2)`
    - Ensures the snake moves every 0.2 seconds.

39. `ClearBackground(green);`
    - Clears the screen with the background color.

40. `DrawRectangleLinesEx(...)`
    - Draws the grid's border.

41. `DrawText(...)`
    - Displays the game title and score.

42. `EndDrawing();`
    - Ends the drawing phase for the current frame.

43. `CloseWindow();`
    - Closes the game window and cleans up resources.

"DONE..."
