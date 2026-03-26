# Rack Modeling

InfraLynx models rack placement with explicit unit coordinates and rack faces.

## Baseline Rules

- rack units must stay within `1..totalUnits`
- device height must be at least `1U`
- device placement must not extend beyond rack capacity
- overlap is invalid only on the same rack face

## Modeling Direction

- front and rear faces are modeled independently
- a device can reserve multiple contiguous units
- rack placement remains separate from cable modeling
- physical occupancy validation should be deterministic and fast

## Deferred Enhancements

Later DCIM work can extend this with:

- zero-U and fractional mounting patterns
- rack elevation rendering metadata
- airflow and environmental attributes
- reserved space planning
