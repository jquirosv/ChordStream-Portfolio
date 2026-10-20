# Technical challenges and decisions

## Chord placement without breaking lyrics

Chords can appear inside words or close together. Treating every chord as an
ordinary inline text fragment can create unwanted spaces and wrapping.

The reader measures the lyric text and places chords in a separate layer. The
regression tests include internal chord anchors, close chord positions, and line
breaks. The editor also keeps the original source visible to the user.

## Transposition without overwriting the arrangement

Changing the performance key should not destroy the original song. The lexer and
parser build a musical tree that can be transformed in memory. Transposition and
instrument filters produce the reading view from that tree.

Chord inversions and extensions, instrument ranges, and tablature constraints
require musical rules beyond replacing note names in a string.

## Personal and collaborative libraries

An individual songbook should remain useful without connectivity. SQLite stores
the local library, while the API manages authenticated group workspaces.

The distinction is visible in the behavior: personal work is local, and remote
group changes require confirmation. The application also keeps workspace data
separated by identity.

## Concurrent changes and retries

Two users can edit the same shared resource. Optimistic revisions identify stale
writes rather than silently replacing newer changes. Idempotency keys distinguish
a retried creation from a new operation. Transactions keep related mutations and
synchronization events consistent.

## Verification

The private implementation includes music-engine, data, state, widget, and visual
regression tests, PHP checks, an OpenAPI contract, and isolated MySQL integration
tests. Visual baselines use a defined rendering environment for reproducibility.

On October 20, 2026, the local verification passed 282 Flutter tests and 31 PHP
tests, together with static analysis, PHP lint, OpenAPI validation, and parity of
60 documented API operations. Device testing remains a separate activity.

[Back to the project overview](../README.md)
