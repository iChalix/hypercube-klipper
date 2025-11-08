# Release Checklist

This document provides a comprehensive checklist for preparing and executing a release of the Hypercube Klipper configuration.

---

## Pre-Release Phase

### Code & Configuration

- [ ] All configuration files tested on hardware
- [ ] All MCUs communicating properly
- [ ] Motion system tested (X, Y, Z axes)
- [ ] Sensorless homing functioning reliably
- [ ] Probe triggering correctly
- [ ] Temperature control stable (PID tuned)
- [ ] All macros tested and working
- [ ] Input shaping calibrated
- [ ] Bed mesh generation successful
- [ ] Z-tilt adjustment working
- [ ] No known critical bugs

### Documentation

- [ ] README.md updated
- [ ] CHANGELOG.md created/updated
- [ ] RELEASE_NOTES.md created
- [ ] RELEASE_v{VERSION}.md created
- [ ] CLAUDE.md reviewed and updated
- [ ] All code comments accurate
- [ ] Pin mappings documented
- [ ] Troubleshooting section complete

### Version Management

- [ ] VERSION file updated
- [ ] Version number follows semantic versioning
- [ ] All version references consistent across files
- [ ] Git tag prepared (v{MAJOR}.{MINOR}.{PATCH})

### Testing

- [ ] **Basic Motion Tests**
  - [ ] X-axis homing
  - [ ] Y-axis homing
  - [ ] Z-axis homing with probe
  - [ ] Manual movement in all directions
  - [ ] Sensorless homing sensitivity verified

- [ ] **Thermal Tests**
  - [ ] Extruder heats to target
  - [ ] Bed heats to target
  - [ ] PID stability verified
  - [ ] Thermal runaway protection tested
  - [ ] Fan control verified

- [ ] **Probing & Leveling Tests**
  - [ ] Probe accuracy test passed
  - [ ] Bed mesh calibration successful
  - [ ] Z-tilt adjustment working
  - [ ] Axis twist compensation applied

- [ ] **Print Tests**
  - [ ] START macro successful
  - [ ] First layer adhesion good
  - [ ] Complete test print (e.g., Benchy)
  - [ ] STOP macro successful
  - [ ] Quality inspection passed

- [ ] **Macro Tests**
  - [ ] START macro
  - [ ] STOP macro
  - [ ] PAUSE/RESUME/CANCEL
  - [ ] LOAD_FILAMENT
  - [ ] UNLOAD_FILAMENT
  - [ ] M600 filament change

- [ ] **Safety Tests**
  - [ ] Emergency stop functions
  - [ ] Thermal runaway triggers correctly
  - [ ] Min/max temperature limits enforced
  - [ ] Filament sensor detection

### Quality Assurance

- [ ] Configuration validated with `SAVE_CONFIG`
- [ ] No error messages in Klipper log
- [ ] All warnings addressed or documented
- [ ] Performance benchmarks recorded
- [ ] Print quality verified (no ringing, good dimensions)

---

## Release Preparation

### Repository Management

- [ ] All changes committed to git
- [ ] Working directory clean (`git status`)
- [ ] All commits have meaningful messages
- [ ] Branch up to date with main/master

### Documentation Finalization

- [ ] CHANGELOG.md reflects all changes
- [ ] RELEASE_NOTES.md highlights key features
- [ ] Installation instructions tested
- [ ] Migration guide reviewed
- [ ] Known issues documented
- [ ] Support information updated

### Asset Preparation

- [ ] Configuration files ready
- [ ] Documentation files ready
- [ ] Example files prepared (if any)
- [ ] Checksums calculated (if applicable)

---

## Release Execution

### Git Operations

- [ ] Create release branch (if applicable)
  ```bash
  git checkout -b release/v{VERSION}
  ```

- [ ] Final commit with release documentation
  ```bash
  git add .
  git commit -m "Release v{VERSION}"
  ```

- [ ] Create annotated git tag
  ```bash
  git tag -a v{VERSION} -m "Release v{VERSION} - {DESCRIPTION}"
  ```

- [ ] Push to remote repository
  ```bash
  git push origin {BRANCH_NAME}
  git push origin v{VERSION}
  ```

### GitHub Release

- [ ] Navigate to repository releases page
- [ ] Click "Draft a new release"
- [ ] Select tag: `v{VERSION}`
- [ ] Set release title: `v{VERSION} - {RELEASE_NAME}`
- [ ] Copy RELEASE_NOTES.md content to description
- [ ] Attach assets (if any):
  - [ ] printer.cfg
  - [ ] Complete documentation package
  - [ ] Example files
- [ ] Mark as "Latest release" (for stable releases)
- [ ] Mark as "Pre-release" (for beta/RC versions)
- [ ] Publish release

### Pull Request (if using PR workflow)

- [ ] Create pull request from release branch
- [ ] Fill PR description with release highlights
- [ ] Request reviews (if applicable)
- [ ] Ensure all CI/CD checks pass
- [ ] Merge to main branch
- [ ] Delete release branch (after merge)

---

## Post-Release Phase

### Verification

- [ ] GitHub release visible and correct
- [ ] Tag created and pushed
- [ ] Documentation accessible
- [ ] Download links working
- [ ] Release notes formatted correctly

### Communication

- [ ] Update project README with latest version
- [ ] Announce release (if applicable):
  - [ ] GitHub Discussions
  - [ ] Community forums
  - [ ] Social media
  - [ ] Mailing list
- [ ] Update documentation site (if exists)

### Monitoring

- [ ] Monitor for bug reports
- [ ] Respond to community feedback
- [ ] Track download/clone statistics
- [ ] Note any immediate issues

### Housekeeping

- [ ] Archive old release notes (if needed)
- [ ] Update issue tracker milestones
- [ ] Close related issues/PRs
- [ ] Plan next release cycle

---

## Release Types

### Major Release (X.0.0)

Indicates breaking changes or major new features.

Additional checklist items:
- [ ] Migration guide from previous major version
- [ ] Breaking changes clearly documented
- [ ] Deprecation notices for removed features
- [ ] Extended testing period
- [ ] Beta/RC phase completed

### Minor Release (0.X.0)

Indicates new features in backward-compatible manner.

Additional checklist items:
- [ ] New features documented
- [ ] Backward compatibility verified
- [ ] Feature toggles tested (if applicable)

### Patch Release (0.0.X)

Indicates backward-compatible bug fixes.

Additional checklist items:
- [ ] Specific bugs fixed documented
- [ ] No new features added
- [ ] Regression testing completed
- [ ] Fast-track testing acceptable

---

## Rollback Plan

In case of critical issues post-release:

- [ ] **Immediate Actions**
  - [ ] Document the critical issue
  - [ ] Assess severity and impact
  - [ ] Communicate to users

- [ ] **Rollback Steps**
  - [ ] Mark release as "Not recommended" on GitHub
  - [ ] Create hotfix branch
  - [ ] Fix critical issue
  - [ ] Release patch version (0.0.X+1)
  - [ ] Update release notes

- [ ] **Prevention**
  - [ ] Document what was missed in testing
  - [ ] Update checklist to prevent recurrence
  - [ ] Review testing procedures

---

## Sign-Off

### Release Manager

- **Name**: _________________
- **Date**: _________________
- **Signature**: _________________

### Technical Reviewer

- **Name**: _________________
- **Date**: _________________
- **Signature**: _________________

### Quality Assurance

- **Name**: _________________
- **Date**: _________________
- **Signature**: _________________

---

## Notes

Use this section for release-specific notes, exceptions, or special considerations:

```
[Add any release-specific notes here]
```

---

## Version-Specific Checklists

### v1.0.0 Release Checklist

Completed: ☑ November 8, 2025

- ☑ Initial stable release
- ☑ Multi-MCU configuration tested
- ☑ All documentation created
- ☑ Macros tested and verified
- ☑ Input shaping calibrated
- ☑ PID values stable
- ☑ Test prints completed successfully
- ☑ CHANGELOG.md created
- ☑ RELEASE_NOTES.md created
- ☑ RELEASE_v1.0.0.md created
- ☑ VERSION file created
- ☑ Git tag v1.0.0 created

---

**Checklist Version**: 1.0
**Last Updated**: November 8, 2025
