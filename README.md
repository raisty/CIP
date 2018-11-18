# CIP
Core Improvement Proposal (CIP) describe standards for the Core platform, including core protocol specifications, client APIs, and contract standards.

A browsable version of all current and draft CIPs can be found on [the official CIP site](https://cip.corecoin.cc/).

# Contributing

 1. Review [What is CIP](doc/what-is-cip.md), [CIP rationale](doc/cip-rationale.md), [CIP types](doc/cip-types.md), [CIP workflow](doc/cip-workflow.md), [CIP editors](doc/cip-editors.md).
 2. Fork the repository by clicking "Fork" in the top right.
 3. Add your CIP to your fork of the repository. There is a [template CIP here](doc/cip-0.md).
 4. Submit a Pull Request to Core's [CIP repository](https://github.com/core-coin/CIP).

Your first PR should be a first draft of the final CIP. It must meet the formatting criteria enforced by the build (largely, correct metadata in the header). An editor will manually review the first PR for a new CIP and assign it a number before merging it. Make sure you include a `discussions-to` header with the URL to a discussion forum or open GitHub issue where people can discuss the CIP as a whole.

If your CIP requires images, the image files should be included in a subdirectory of the `assets` folder for that CIP as follow: `assets/images/cip-X` (for CIP **X**). When linking to an image in the CIP, use relative links such as `../assets/images/cip-X/image.png`.

Once your first PR is merged, we have a bot that helps out by automatically merging PRs to draft CIPs. For this to work, it has to be able to tell that you own the draft being edited. Make sure that the 'author' line of your CIP contains either your Github username or your email address inside <triangular brackets>. If you use your email address, that address must be the one publicly shown on [your GitHub profile](https://github.com/settings/profile).

When you believe your CIP is mature and ready to progress past the draft phase, you should do one of two things:

 - **For a Standards Track CIP of type Core**, discuss your implementation in [Core Talk](https://coretalk.info/c/cip/vetting), where it can be vetted for inclusion in a future hard fork. If implementers agree to include it, the CIP editors will update the state of your CIP to 'Accepted'.
 - **For all other CIPs**, open a PR changing the state of your CIP to 'Final'. An editor will review your draft and ask if anyone objects to its being finalised. If the editor decides there is no rough consensus - for instance, because contributors point out significant issues with the CIP - they may close the PR and request that you fix the issues in the draft before trying again.

# CIP Status Terms

* <kbd>Draft</kbd> - a CIP that is undergoing rapid iteration and changes
* <kbd>Last Call</kbd> - a CIP that is done with its initial iteration and ready for review by a wide audience
* <kbd>Accepted</kbd> - a core CIP that has been in Last Call for at least 2 weeks and any technical changes that were requested have been addressed by the author
* <kbd>Final (non-Core)</kbd> - a CIP that has been in Last Call for at least 2 weeks and any technical changes that were requested have been addressed by the author.
* <kbd>Final (Core)</kbd> - a CIP that the Core Devs have decide to implement and release in a future hard fork or has already been released in a hard fork
* <kbd>Deferred</kbd> - a CIP that is not being considered for immediate adoption. May be reconsidered in the future for a subsequent hard fork.

# Preferred Citation Format

The canonical URL for a CIP that has achieved draft status at any point is at https://cip.corecoin.cc/. For example, the canonical URL for CRC-X is https://cip.corecoin.cc/CIP/cip-X (for CRC **X**).

# Channels

* [Core Talk](https://coretalk.info)
* [Discord chat](https://coretalk.info/discord)
* [Subreddit](https://www.reddit.com/r/CoreCoinCC/)
