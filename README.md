# Project Vector

Project Vector is a reference prototype for a tabletop smart-city model controlled by an Arduino Opta PLC and represented by a connected digital twin.

## Current phase

The physical city model is not yet built. The immediate goal is to design and construct a small, testable city block before connecting it to the digital twin, VECTOR catalog, and Backstage.

## Project goal

Build a demonstrator that:

- controls a visible physical city process with an Arduino Opta PLC;
- exposes selected state through Modbus TCP;
- mirrors the physical system in a digital twin; and
- makes the physical asset and twin discoverable through VECTOR and Backstage.

## Initial physical scenario

The recommended first build is a smart intersection with:

- two-direction vehicle traffic lights;
- pedestrian signals and a crossing button;
- streetlights controlled by an ambient-light sensor;
- optional traffic or occupancy sensing; and
- an optional parking barrier or gate.

The emphasis is a reliable, observable system—not a large or highly detailed model.

## Architecture

```text
Physical city model
  ↕ sensors and actuators
Arduino Opta PLC
  ↕ Modbus TCP
Digital twin
  ↕
VECTOR catalog and Backstage
```

The Arduino Opta remains the authority for physical control and safe sequencing. The digital twin reports state and can send only approved requests; it must not bypass PLC safety logic.

## Phased scope

1. **Define the reference architecture** — component relationship, data contract, and endpoint configuration.
2. **Build the city model** — construct the intersection, indicators, button, lights, and selected sensors.
3. **Configure the Opta** — create the I/O map and implement the traffic-light state machine.
4. **Implement Modbus TCP** — expose documented states, health signals, and approved requests.
5. **Create the digital twin** — map twin properties to the PLC register contract.
6. **Integrate VECTOR and Backstage** — catalog physical and digital components and prototype deployment or configuration.
7. **Test and document** — validate normal operation, faults, reconnects, and endpoint switching.

## Recommended build order

1. Select the first city scenario.
2. Build one small physical subsystem.
3. Test one PLC input and output.
4. Implement the intersection state machine.
5. Add pedestrian and streetlight behavior.
6. Verify the physical model independently.
7. Define and test the Modbus register map.
8. Connect the digital twin.
9. Add VECTOR and Backstage integration.
10. Run an end-to-end demonstration.

## Safety note

This is a reference prototype, not a production industrial control system. Use appropriate power supplies, load drivers, wiring protection, and enclosures. Verify electrical requirements before connecting loads to PLC outputs.
