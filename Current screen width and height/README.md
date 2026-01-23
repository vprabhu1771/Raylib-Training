```cpp
#include "raylib.h"
#include <iostream>

int main()
{
	const int screenWidth = 800;
	const int screenHeight = 600;

	const char* title = "Raylib Window sss";	

	InitWindow(screenWidth, screenHeight, title);

	// Get current screen width
	std::cout << "Current Screen Width " << GetScreenWidth() << std::endl;

	// Get current screen height
	std::cout << "Current Screen Height " << GetScreenHeight() << std::endl;

	while (!WindowShouldClose())
	{
		BeginDrawing();
		ClearBackground(RAYWHITE);
		DrawText("Hello, Raylib!", 350, 280, 20, LIGHTGRAY);
		EndDrawing();
	}

	CloseWindow();

	return 0;
}
```

# Output
```
Current Screen Width 800
Current Screen Height 600
```