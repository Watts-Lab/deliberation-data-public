# `preregistration`

This folder contains preregistration records for each datapoint collected on the deliberation-lab platform.

There is one file per experiment batch, with each row representing a separate preregistration record.

Records are generated when participants are randomized to groups, and assigned a treatment condition. They are stored locally and changes are pushed to Github every 60 seconds.

There is one record per datapoint, equivalently one record per participant session. (i.e. if a group discussion has 4 members, there will be 4 records preregistered) containing:

- `sampleId` - a unique identifier that can be used to link this sample preregistration with the eventually released datapoint
- `deliberationId` - a unique identifier for the participant that persists across all sessions the participant joins
- `batchId` - a unique identifier for the experiment batch. Participants arriving in the same batch are recruited from the same pool and are randomized together into groups
- `timeBatchInitialized` - unix epoch time that the experiment batch was created by the experimenter. This timestamp is present in filenames associated with the batch, to keep batches sequential
- `gameId` - a unique identifier for the particular group participants are randomized into for this trial. All participants in the group have the same `gameId`
- `config` - the batch setup options
- `timeStarted` - a unix epoch timestamp for the time when players were randomized into groups, assigned treatments, and entered the synchronous portion of the experiment with their group
- `position` - zero-based integer index of the participant's position within the group. Different positions may be assigned different instructions, etc.
- `treatmentMetadata` - information about the treatment condition including:
  - `name` - the experimenter-assigned name for the treatment
  - `desc` - the experimenter-assigned description of the treatment
  - `playerCount` - the number of participants in the treatment
  - `treatmentHash` - a hex digest of a sha1 hash of the json stringified treatment object, which can be compared against the treatment object in released datafiles to guarantee consistency
- `exportErrors` - a list of any errors encountered in exporting the data, if any
