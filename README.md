# Claude Code Skills Collection

A collection of custom skills for [Claude Code](https://github.com/anthropics/claude-code) to enhance development workflows.

## Available Skills

### 🚀 java-upgrade

Automate the upgrade of Java Maven projects from Java 8/11/17 and Spring Boot 2.x to Java 21 and Spring Boot 3.x.

**Features:**
- ☕ Java version upgrade to 21
- 🚀 Spring Boot upgrade to 3.x
- 📦 Jakarta EE namespace migration (javax.* → jakarta.*)
- 🔧 Dependency compatibility updates
- 🔒 Spring Security 6 migration
- 💾 Hibernate 6 compatibility

**Usage:** `/java-upgrade`

[Read more →](./java-upgrade/README.md)

## Installation

### Install All Skills

Clone this repository to your Claude Code skills directory:

```bash
# Backup your existing skills (if any)
mv ~/.config/opencode/skill ~/.config/opencode/skill.backup

# Clone this repository
git clone https://github.com/Joseph19820124/opencode-skills.git ~/.config/opencode/skill
```

### Install Individual Skills

You can also install individual skills:

```bash
cd ~/.config/opencode/skill

# Install java-upgrade skill
git clone https://github.com/Joseph19820124/opencode-skills.git temp
mv temp/java-upgrade ./
rm -rf temp
```

## Usage

In your Claude Code session, you can use any skill by typing:

```bash
/skill-name
```

For example:
```bash
/java-upgrade
```

## Creating Your Own Skills

Each skill is a directory containing a `SKILL.md` file with the following structure:

```markdown
---
name: skill-name
description: Brief description of what the skill does
license: MIT
compatibility: opencode
metadata:
  key: value
---

# Skill Title

Detailed instructions and steps for the skill...
```

### Skill Directory Structure

```
skill-name/
├── SKILL.md          # Required: Skill definition and instructions
├── README.md         # Optional: Documentation for users
└── LICENSE           # Optional: License file
```

### Adding Your Skill to This Collection

1. Fork this repository
2. Create a new directory for your skill
3. Add `SKILL.md` with your skill instructions
4. Update this README.md to include your skill
5. Submit a Pull Request

## Contributing

Contributions are welcome! Here's how you can help:

1. **Add New Skills**: Create new skills for common development tasks
2. **Improve Existing Skills**: Enhance documentation or functionality
3. **Report Issues**: Found a bug? Let us know!
4. **Share Ideas**: Suggest new skills or improvements

### How to Contribute

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingSkill`)
3. Commit your changes (`git commit -m 'Add some AmazingSkill'`)
4. Push to the branch (`git push origin feature/AmazingSkill`)
5. Open a Pull Request

## Skill Ideas

Looking for inspiration? Here are some skill ideas:

- 🐳 **docker-compose-generator**: Generate docker-compose.yml for common stacks
- 🧪 **test-coverage-improver**: Analyze and improve test coverage
- 📝 **api-doc-generator**: Generate API documentation from code
- 🔍 **code-reviewer**: Automated code review with best practices
- 🌐 **i18n-setup**: Set up internationalization for web apps
- 🔐 **security-audit**: Security vulnerability scanning and fixes
- 📊 **performance-analyzer**: Identify and fix performance bottlenecks

## Resources

- [Claude Code Documentation](https://github.com/anthropics/claude-code)
- [Creating Skills Guide](https://github.com/anthropics/claude-code#skills)

## License

This collection is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Individual skills may have their own licenses - check each skill's directory.

## Support

If you encounter any issues:

- 🐛 [Open an issue](https://github.com/Joseph19820124/opencode-skills/issues)
- 💬 Check existing issues and discussions
- 📖 Review the [Claude Code documentation](https://github.com/anthropics/claude-code)

## Acknowledgments

Built for use with [Claude Code](https://github.com/anthropics/claude-code) by Anthropic.

---

Made with ❤️ by the community
