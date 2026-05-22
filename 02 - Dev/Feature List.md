Current Feature Inventory
Already Shipped
- Views: Inbox, Timeline (replaces Today), Completed — with sidebar and bottom nav
- Projects: Default seeds (Inbox/Work/Personal/Ideas), create/rename/recolor, sidebar list
- Tasks: Create, edit, complete, uncomplete, delete, reorder, undo (with 5s snackbar)
- Recurring tasks: Daily/weekly/monthly/yearly (self-recurring model)
- Date parsing: Rich NLP — relative ("in 5 min"), absolute ("friday at 3pm"), keywords ("tod", "2moro"), short days ("wed"), numeric ("21/05"), text dates ("may 21")
- Syntax highlighting: Priority (red), projects (purple), dates (green), times (blue), recurrence (green)
- Notifications: macOS via flutter_local_notifications, Android/iOS via alarm
- Search: Cmd+K search bar in sidebar
- Keyboard shortcuts: Cmd+N, Cmd+K, Cmd+1/2/3, Cmd+Z (macOS)
- Android widget: Task list with colored project labels and pill styling
- Project pills: Colored project badges in task tiles
- Time pills: Time shown as pill on inbox, project, and timeline views
Not Yet Built
Near-term (natural extensions):
1. Custom recurrence intervals: Specific days of week ("every mon/wed/fri"), end dates, "every weekday"
2. Calendar grid view: Full month calendar with task dots
3. Timeline drag-to-reorder: Reorder tasks by dragging in timeline view
4. Task description UI: Description field exists in model but needs proper expandable sheet or inline editor
5. Task copy/duplicate: No duplicate action yet
6. Batch operations: Multi-select tasks for bulk complete/delete/move
7. Pin/archive projects: Pin to top of sidebar, archive (hide)
8. Completed task cleanup: "Clear completed" button for inbox/projects
9. Swipe actions: Mobile swipe-to-complete/delete (iOS/Android)
Future phases (from CLAUDE.md):
10. Phase 4 — Sync engine: Last-write-wins → CRDT for offline sync across devices
11. Phase 5 — Axum/PostgreSQL backend: Cloud server
Stretch:
12. Labels/tags: Beyond projects, free-form tagging
13. Subtasks/checklists: Hierarchical task breakdown
14. Focus mode / Pomodoro timer
15. iOS widget: Widget for iOS
16. Theme customization: Allow light theme or accent color selection
17. Export/import: JSON/CSV export, Todoist migration import
18. Calendar integration: Read events from system calendar
Want me to scope any of these for implementation?