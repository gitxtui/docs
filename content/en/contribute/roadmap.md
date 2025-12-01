---
title: "Project Roadmap"
weight: 1
type: "docs"
---

<style>
.roadmap-container {
  margin: 2rem 0;
}

.roadmap-section {
  position: relative;
  padding: 1.5rem;
  margin-bottom: 2rem;
  border-left: 4px solid;
  border-radius: 4px;
  transition: background-color 0.3s, border-color 0.3s;
}

/* Light theme */
.roadmap-section.done {
  border-color: #28a745;
  background: #f0f9f4;
}

.roadmap-section.active {
  border-color: #007bff;
  background: #e7f3ff;
}

.roadmap-section.planned {
  border-color: #6c757d;
  background: #f8f9fa;
}

/* Dark theme */
@media (prefers-color-scheme: dark) {
  .roadmap-section.done {
    border-color: #4ade80;
    background: rgba(74, 222, 128, 0.1);
  }

  .roadmap-section.active {
    border-color: #3b82f6;
    background: rgba(59, 130, 246, 0.1);
  }

  .roadmap-section.planned {
    border-color: #9ca3af;
    background: rgba(156, 163, 175, 0.1);
  }
}

/* Docsy dark mode class support */
.td-dark .roadmap-section.done {
  border-color: #4ade80;
  background: rgba(74, 222, 128, 0.1);
}

.td-dark .roadmap-section.active {
  border-color: #3b82f6;
  background: rgba(59, 130, 246, 0.1);
}

.td-dark .roadmap-section.planned {
  border-color: #9ca3af;
  background: rgba(156, 163, 175, 0.1);
}

.roadmap-section h3 {
  margin-top: 0;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.roadmap-section ul {
  margin-bottom: 0;
}

.roadmap-section li {
  margin: 0.75rem 0;
}

.status-badge {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  border-radius: 12px;
  font-size: 0.85rem;
  font-weight: 600;
}

/* Light theme badges */
.status-badge.done {
  background: #28a745;
  color: white;
}

.status-badge.active {
  background: #007bff;
  color: white;
}

.status-badge.planned {
  background: #6c757d;
  color: white;
}

/* Dark theme badges */
@media (prefers-color-scheme: dark) {
  .status-badge.done {
    background: #4ade80;
    color: #0f172a;
  }

  .status-badge.active {
    background: #3b82f6;
    color: white;
  }

  .status-badge.planned {
    background: #9ca3af;
    color: #0f172a;
  }
}

/* Docsy dark mode class support for badges */
.td-dark .status-badge.done {
  background: #4ade80;
  color: #0f172a;
}

.td-dark .status-badge.active {
  background: #3b82f6;
  color: white;
}

.td-dark .status-badge.planned {
  background: #9ca3af;
  color: #0f172a;
}
</style>

<div class="roadmap-container">

<div class="roadmap-section done">
  <h3>✅ Completed <span class="status-badge done">Done</span></h3>
  <ul>
    <li><strong>Basic TUI Structure:</strong> A foundational terminal user interface is in place, providing the core layout and panel management for the application.</li>
    <li><strong>Git Command Mapping:</strong> Essential Git commands are integrated into the TUI, allowing users to perform basic operations visually.</li>
    <li><strong>Theme Generation:</strong> The application can generate themes from a predefined set of color palettes, allowing for initial UI customization.</li>
    <li><strong>Custom Theme Support:</strong> Implement a system for users to add their own themes via configuration files in the <code>.config</code> directory.</li>
    <li><strong>Expanded Git Command Support:</strong> Integrate a wider range of Git commands to provide more comprehensive repository management capabilities.</li>
    <li><strong>Bug Fixes:</strong> Address any outstanding bugs to improve stability and reliability.</li>
    <li><strong>Command History and Logging:</strong> Allow the secondary panel to store all the git commands history and gitx logs.</li>
  </ul>
</div>

<div class="roadmap-section active">
  <h3>🚀 In Progress <span class="status-badge active">Active</span></h3>
  <ul>
    <li><strong>Items will be moved here soon from the planned section</strong>
  </ul>
</div>

<div class="roadmap-section planned">
  <h3>📋 Planned <span class="status-badge planned">Upcoming</span></h3>
  <ul>
    <li><strong>Repository Initialization:</strong> Add a feature that allows users to initialize a new Git repository in the current directory if one doesn't already exist.</li>
    <li><strong>Safety Warnings:</strong> Implement a warning system to alert users when they are about to initialize a repository in a potentially problematic location.</li>
    <li><strong>Improved Visual Diff Viewer:</strong> Enhance the diff viewer to provide a more intuitive and detailed representation of changes.</li>
    <li><strong>Interactive Staging:</strong> Allow users to stage and unstage individual lines or hunks of code directly from the visual diff viewer.</li>
    <li><strong>Merge Conflict Resolver:</strong> Build a tool to help users resolve merge conflicts from within the TUI.</li>
    <li><strong>Custom Keybindings:</strong> Update config.toml logic to allow users to remap keys (currently hardcoded in keys.go).</li>
  </ul>
</div>

</div>
