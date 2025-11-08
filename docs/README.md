# Documentation Directory

This directory contains comprehensive documentation for the Hypercube Klipper configuration project.

## Contents

### Release Documentation

- **[RELEASE_v1.0.0.md](RELEASE_v1.0.0.md)** - Complete release documentation for version 1.0.0
  - Executive summary
  - Hardware and software requirements
  - Feature descriptions with technical details
  - Installation and migration guides
  - Testing and validation procedures
  - Troubleshooting guide
  - Performance metrics
  - Security considerations

- **[RELEASE_CHECKLIST.md](RELEASE_CHECKLIST.md)** - Comprehensive release checklist
  - Pre-release phase tasks
  - Release preparation steps
  - Release execution procedures
  - Post-release verification
  - Rollback plan

## Quick Links

### For Users

- **Getting Started**: See [README.md](../README.md) in the root directory
- **Installation**: Refer to [RELEASE_v1.0.0.md](RELEASE_v1.0.0.md#installation-guide)
- **Troubleshooting**: Check [RELEASE_v1.0.0.md](RELEASE_v1.0.0.md#troubleshooting)
- **Release Notes**: See [RELEASE_NOTES.md](../RELEASE_NOTES.md) for highlights

### For Developers

- **Contributing**: See [CLAUDE.md](../CLAUDE.md) for development guidelines
- **Changelog**: Review [CHANGELOG.md](../CHANGELOG.md) for all changes
- **Release Process**: Follow [RELEASE_CHECKLIST.md](RELEASE_CHECKLIST.md)

## Documentation Structure

```
hypercube-klipper/
├── README.md                    # Main user documentation
├── CLAUDE.md                    # Development guidelines
├── CHANGELOG.md                 # Version history and changes
├── RELEASE_NOTES.md            # Current release highlights
├── VERSION                      # Current version number
├── config/
│   └── printer.cfg             # Main Klipper configuration
└── docs/
    ├── README.md               # This file
    ├── RELEASE_v1.0.0.md      # Detailed release documentation
    └── RELEASE_CHECKLIST.md   # Release process checklist
```

## Documentation Standards

### Release Documentation

Each major or minor release should have:
1. Dedicated release document (RELEASE_vX.Y.Z.md)
2. Updated CHANGELOG.md entry
3. Updated RELEASE_NOTES.md for latest release
4. VERSION file update

### Document Format

- Use Markdown format
- Include table of contents for long documents
- Use consistent heading levels
- Include code blocks with syntax highlighting
- Add tables for structured data
- Include links to related documentation

## Version Information

**Current Version**: 1.0.0
**Release Date**: November 8, 2025
**Release Type**: Initial Public Release

See [VERSION](../VERSION) file for current version number.

## Additional Resources

### External Documentation

- **Klipper Official Docs**: https://www.klipper3d.org/
- **Klipper Config Reference**: https://www.klipper3d.org/Config_Reference.html
- **TMC Driver Guide**: https://www.klipper3d.org/TMC_Drivers.html
- **Input Shaping Guide**: https://www.klipper3d.org/Resonance_Compensation.html
- **Cartographer Probe**: https://docs.cartographer3d.com/

### Community Resources

- **GitHub Repository**: https://github.com/iChalix/hypercube-klipper
- **Issue Tracker**: https://github.com/iChalix/hypercube-klipper/issues
- **Hypercube Community**: Tech2C forums and Discord

## Maintenance

### Updating Documentation

When making changes:
1. Update relevant documentation files
2. Update VERSION file if releasing
3. Add entry to CHANGELOG.md
4. Update this README if structure changes
5. Review all cross-references and links

### Documentation Review Schedule

- **After each release**: Update all release-related docs
- **Monthly**: Review for accuracy and completeness
- **Quarterly**: Major documentation review and cleanup

## Contact & Support

For questions or issues with documentation:
- Open an issue on GitHub
- Check existing documentation first
- Review Klipper official documentation
- Consult community forums

---

**Last Updated**: November 8, 2025
**Maintained By**: iChalix/hypercube-klipper project
