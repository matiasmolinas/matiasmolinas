# Matías Molinas

I work on the part of agent systems that nobody demos: not whether an agent can do
something, but how you would know it did.

Most of it happens at **[Evolving Agents Labs](https://github.com/EvolvingAgentsLabs)**,
out of an ongoing conversation with **[Ismael Faro](https://github.com/ismaelfaro)** —
the ideas, the architecture and the code. The repositories are where those
conversations get tested.

### Three things that kept working

**Constrain the mechanism, not the prompt.**
[token-trie](https://github.com/EvolvingAgentsLabs/token-trie) masks the sampler's
valid-next set at every decoding step, so a 350M model playing Tetris in a browser tab
*cannot* emit malformed syntax — the parser downstream is a plain regex with no repair
path, because it does not need one. The matched negative is what convinced me: the
prompt-level version of the same objective fires in 1 of 7 identical sessions, and
instructing harder measured worse.

**Prove it, then freeze it.**
[agentvcs](https://github.com/EvolvingAgentsLabs/agentvcs) versions an agent's code,
goal, model pins, trace and sub-agent swarm in one commit, and `freeze` refuses unless
the declared eval passes — forcing past a failure stamps `verified: false` rather than
quietly lying. Conflicts between what an agent taught itself at runtime and what a team
edited in git go to a reconciler over a plain stdin/stdout contract.

**Look where the standard filter is blind.**
[sleep-harness](https://github.com/EvolvingAgentsLabs/sleep-harness) reads a model's
residual stream to catch memory-injection payloads written in words a keyword filter
likes. Nine hard pairs at 0.657 lexical overlap, p=0.0195; an adapter trojan scanner at
12/12, p=0.0002.

### And what didn't

sleep-harness pre-registers its hypotheses. Its founding one — that filtering by
internal workspace beats filtering by output — is marked **REFUTADA**, and the free
lexical baseline significantly outperformed it. I have also published a retraction: a
claim built on a single sample that reversed when re-run.

Publishing the negative results costs nothing and is the only reason the positive ones
are worth reading.

### Elsewhere

[evolving-robot](https://github.com/EvolvingAgentsLabs/evolving-robot) — a ward robot
that misses a fallen patient, rewrites the skill that caused it, and has the rewrite
reverted if it scores worse ·
[skillos](https://github.com/EvolvingAgentsLabs/skillos) — an OS written in markdown ·
[qa](https://github.com/EvolvingAgentsLabs/qa) — a test suite that tells you which
checks you quietly stopped making ·
[evolving-agents](https://github.com/matiasmolinas/evolving-agents) — the earlier
toolkit this grew out of

Before agents: 3D medical visualization, ML for healthcare, and prompt workflow engines
before that was a category.

**[The through-line, written out →](https://evolvingagentslabs.github.io/thesis/)**

<sub>Talk to me about constrained decoding, evaluating self-modifying systems, or why
your agent's memory needs a firewall. <a href="https://twitter.com/matiasmolinas">@matiasmolinas</a></sub>
