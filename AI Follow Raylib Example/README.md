# Follow "AI" with Raylib 
```
https://www.youtube.com/watch?v=zYnHVR3Po6I
```

Got it — you want a simple **AI that follows a target using Raylib** 👾
Classic and fun. Let’s do a **clean, beginner-friendly Raylib (C) example** where an enemy smoothly follows the player.

---

## 🎯 Concept (very simple AI)

* Player moves with **WASD**
* AI computes direction toward player
* AI moves a little every frame → smooth following

---

## 🧠 Core Logic

```c
direction = normalize(playerPos - enemyPos);
enemyPos += direction * speed * deltaTime;
```

That’s the whole “AI” brain 😄

---

## ✅ Full Working Raylib Example (C)

```c
#include "raylib.h"
#include <math.h>

int main(void)
{
    const int screenWidth = 800;
    const int screenHeight = 450;

    InitWindow(screenWidth, screenHeight, "Raylib AI Follow Example");
    SetTargetFPS(60);

    Vector2 playerPos = { 400, 225 };
    Vector2 enemyPos  = { 100, 100 };

    float playerSpeed = 200.0f;
    float enemySpeed  = 120.0f;

    while (!WindowShouldClose())
    {
        float dt = GetFrameTime();

        // ---- Player Movement ----
        if (IsKeyDown(KEY_W)) playerPos.y -= playerSpeed * dt;
        if (IsKeyDown(KEY_S)) playerPos.y += playerSpeed * dt;
        if (IsKeyDown(KEY_A)) playerPos.x -= playerSpeed * dt;
        if (IsKeyDown(KEY_D)) playerPos.x += playerSpeed * dt;

        // ---- AI Follow Logic ----
        Vector2 direction = {
            playerPos.x - enemyPos.x,
            playerPos.y - enemyPos.y
        };

        float length = sqrtf(direction.x * direction.x + direction.y * direction.y);

        if (length > 1.0f) // avoid jitter
        {
            direction.x /= length;
            direction.y /= length;

            enemyPos.x += direction.x * enemySpeed * dt;
            enemyPos.y += direction.y * enemySpeed * dt;
        }

        // ---- Draw ----
        BeginDrawing();
        ClearBackground(RAYWHITE);

        DrawCircleV(playerPos, 15, BLUE);
        DrawCircleV(enemyPos, 15, RED);

        DrawText("WASD to move player", 10, 10, 20, DARKGRAY);
        DrawText("Red circle follows Blue circle", 10, 40, 20, DARKGRAY);

        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## 🧪 Easy Improvements (next steps)

You can level this up fast:

### 🧍‍♂️ Stop at distance

```c
if (length > 60)
```

### 🧠 Smarter AI

* Line-of-sight check
* Chase only if player is close
* Patrol → Chase → Attack states (FSM)

### 🧲 Smooth follow (lerp)

```c
enemyPos = Vector2Lerp(enemyPos, playerPos, 0.02f);
```

---

## 🔥 Want more?

I can show you:

* 🧠 **State-based AI** (Idle / Chase / Attack)
* 🧭 **Pathfinding (A*)**
* 🎮 **Top-down shooter AI**
* 🧟 **Zombie swarm behavior**
* 🧩 **Raylib + C++ or Python version**

Just tell me what kind of game you’re building 😎
