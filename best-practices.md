# asyncio Best Practices (Based on Documentation & aiohttp)

- **Use `asyncio.run()` for top‑level entry points** – It creates and closes the event loop safely.
- **Prefer high‑level APIs** – Functions like `asyncio.gather`, `asyncio.wait`, and `asyncio.create_task` simplify concurrency management.
- **Avoid blocking calls** – Off‑load CPU‑bound work to executors via `loop.run_in_executor`.
- **Handle cancellation properly** – Catch `asyncio.CancelledError` and perform necessary cleanup.
- **Leverage async context managers** – Resources such as network connections should be acquired with `async with`.
- **Structure code with `async`/`await`** – Keep coroutines small and composable; avoid deep nesting.
- **Use `asyncio.Queue` for producer/consumer patterns** – It provides built‑in synchronization.
- **Apply timeout handling** – Wrap operations with `asyncio.wait_for` to prevent indefinite hangs.
- **Document public API** – Export symbols via `__all__` and provide type hints for better maintainability.
- **Lazy‑load optional heavy dependencies** – As shown in aiohttp’s `__getattr__`, defer imports until needed to speed up startup.

Following these guidelines will lead to more robust and maintainable asynchronous Python code.
