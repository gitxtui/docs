---
title: "How to Contribute a Blog Post to GITx Documentation"
linkTitle: "Contributing Blog Posts"
date: 2025-10-02
description: "A step-by-step guide on how to write and submit your first blog post to the GITx documentation site."
author: "bakayu"
---

Welcome to the GITx blog! We're excited to have you here and even more excited if you're thinking about contributing your own post. This guide will walk you through the entire process of creating and submitting a blog post to our documentation site.

## What Should You Write About?

We welcome blog posts on any topic related to Git! Here are some ideas to get you started:

- **Git Commands Deep Dive**: Explain a specific Git command in detail (like `git bisect`, `git rebase`, or `git cherry-pick`)
- **Git Workflows**: Share best practices for team collaboration using Git
- **Git History & Fun Facts**: Interesting trivia about Git's development or its creator
- **Personal Stories**: How Git helped you solve a problem or improved your workflow
- **Tips & Tricks**: Lesser-known Git features that make developers more productive
- **Tutorials**: Step-by-step guides for achieving specific tasks with Git

## Step-by-Step: How to Contribute

### 1. Fork the Repository

Start by forking the [`gitxtui/docs`](https://github.com/gitxtui/docs) repository on GitHub. Click the "Fork" button in the top-right corner of the repository page.

```bash
# Clone your forked repository
git clone https://github.com/YOUR_USERNAME/docs.git
cd docs
```

### 2. Create Your Blog Post File

Navigate to the blog directory and create a new Markdown file:

```bash
cd content/en/blog
touch my-awesome-git-post.md
```

Choose a descriptive filename using lowercase letters and hyphens (e.g., `git-rebase-explained.md`, `my-first-git-contribution.md`).

### 3. Add the Front Matter

Every blog post needs front matter at the top. This is metadata that Hugo (our static site generator) uses to organize and display your post. Here's the required format:

```markdown
---
title: "Your Blog Post Title"
linkTitle: "Short Title"
date: 2025-10-02
description: "A brief description of what your post is about (1-2 sentences)."
author: "Your Name or GitHub Username"
---
```

**Explanation:**
- `title`: The full title that appears at the top of your post
- `linkTitle`: A shorter version for navigation menus
- `date`: The publication date (use today's date)
- `description`: A brief summary for SEO and previews
- `author`: Your name or GitHub username

### 4. Write Your Content

Now comes the fun part! Write your blog post using Markdown. Here are some formatting tips:

**Headers:**
```markdown
# Heading 1
## Heading 2
### Heading 3
```

**Code Blocks:**
````markdown
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```
````

**Emphasis:**
````markdown
**bold text**
*italic text*
`inline code`
````

**Links:**
````markdown
[link text](https://example.com)
````

### 5. Preview Your Post Locally

If you want to see how your post looks before submitting, you can run Hugo locally:

```sh
# From the docs root directory
hugo server -D
```

hen open [http://localhost:1313/docs/blog](http://localhost:1313/docs/blog) in your browser to preview your post.

### 6. Submit Your Pull Request

Once you're happy with your post, it's time to submit it:

```sh
# switch to a new branch
git switch -c docs-add-blog

# Add your new file
git add content/en/blog/my-awesome-git-post.md

# Commit with a descriptive message
git commit -m "feat: Add blog post about [your topic]"

# Push to your fork
git push origin docs-add-blog
```

Now go to GitHub and create a pull request from your fork to the main [`gitxtui/docs`](https://github.com/gitxtui/docs) repository. In your PR description, briefly explain what your blog post is about.

### 7. Review Process

After you submit your PR:

- Our team will review your submission
- We may provide feedback or suggestions for improvement
- Once everything looks good, we'll merge your post
- Your contribution will be live on the GITx documentation site! 🎉

Tips for Great Blog Posts:

- Keep it focused: Cover one main topic per post
- Use examples: Code examples and real-world scenarios help readers understand
- Break it up: Use headers, lists, and short paragraphs for readability
- Proofread: Check for typos and grammar issues before submitting
- Be friendly: Write in a conversational tone—imagine you're explaining to a friend
- Need Help?

If you have questions or need assistance:

- Open an issue on the [gitxtui/docs](https://github.com/gitxtui/docs) repository
- Join our [Discord community](https://discord.gg/DphdFXd3Bh)
- Comment on the [blog contribution issue](https://github.com/gitxtui/docs/issues/13)

We can't wait to read your contribution! Happy writing! ✍️
