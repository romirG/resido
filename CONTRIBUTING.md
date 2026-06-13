# Contributing to ResiDo

Thank you for your interest in contributing! 🎉

## Getting Started

1. **Fork** this repository on GitHub
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/your-username/resido.git
   cd resido
   ```
3. **Set up** the project by following the [Quick Start](README.md#-quick-start) instructions in the README.

## Development Workflow

```bash
# Create a feature branch from main
git checkout -b feature/your-feature-name

# Make your changes, then stage and commit
git add .
git commit -m "feat: add your feature description"

# Push to your fork
git push origin feature/your-feature-name
```

Then open a **Pull Request** on GitHub targeting the `main` branch.

## Commit Message Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/):

| Prefix | Use for |
|--------|---------|
| `feat:` | New features |
| `fix:` | Bug fixes |
| `docs:` | Documentation changes |
| `style:` | CSS / formatting (no logic change) |
| `refactor:` | Code restructuring |
| `chore:` | Build / config / tooling |

## Code Style

- **Frontend**: React functional components, Vanilla CSS (no Tailwind)
- **Backend**: Express.js controllers, Sequelize models
- Use meaningful variable names and add comments for complex logic

## Reporting Issues

- Use the [GitHub Issues](https://github.com/romirG/resido/issues) tab
- Include steps to reproduce, expected vs actual behaviour, and environment details

## Questions?

Open a [Discussion](https://github.com/romirG/resido/discussions) or raise an issue — we're happy to help!
