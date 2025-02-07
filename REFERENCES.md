```

````markdown
# References

## CANboat PGN Database
The complete PGN reference documentation can be found at:
https://canboat.github.io/canboat/canboat.html

This database contains:
- Complete PGN number mappings
- Field definitions 
- Data types
- Ranges
- Units
- Resolutions

## Key PGNs Used

### Autopilot PGNs
- 127237 - Heading/Track Control
- 127245 - Rudder
- 127250 - Vessel Heading 
- 128275 - Distance Log
- 65341 - Wind Target (B&G specific)

### System PGNs
- 59904 - ISO Request
- 60928 - ISO Address Claim
- 126720 - Proprietary

## Using PGN Reference
When adding new PGN support:
1. Look up PGN in reference database
2. Note field definitions and data types
3. Implement encode/decode functions
4. Add validation based on ranges
5. Use proper units/scaling

## Example
```javascript
// Looking up PGN 127250 (Vessel Heading)
// Fields:
// - SID (8 bits)
// - Heading (16 bits, rad, resolution 0.0001)
// - Deviation (16 bits)
// - Variation (16 bits) 
// - Reference (2 bits)