## Summary

## What changed?

- [ ] A member concept under `.lokf/knowledge/members/` (a bundle joins, leaves, or moves to a new release)
- [ ] The domain, the policy or the schema (`.lokf/knowledge/domains/`, `policies/`, `.lokf/domain.yaml`)
- [ ] Repository packaging only (CI, templates, docs)

## Checklist

- [ ] `cd .lokf && just lokf-check-refs` and `bash scripts/knowledge-conventions.sh knowledge` pass
- [ ] A member names the newest release that carries a `knowledge-*.zip`, and its checksum is the one in that release's `.sha256`
- [ ] If this pull request records a confirmation: *I opened the release named by every confirmation I am approving.*
- [ ] `CHANGELOG.md` has an entry under `## [Unreleased]` when behaviour changes

## AI Assistance

If you used AI tools while preparing this pull request, you are still the author and responsible for understanding, verifying, and defending your submission. Please engage with reviewers personally rather than through your agent during feedback and revisions. See the [AI Covenant](../AI_COVENANT.md) for details.
