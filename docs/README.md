# Crowbar circuit

Retrieved from: https://en.wikibooks.org/wiki/Practical_Electronics/Crowbar_circuit

A crowbar circuit is a method of protecting a circuit against high voltages
(overvoltage) in the event of a power supply malfunction or power surge.
This is especially useful in a device using TTL components as these are very
sensitive to overvoltage.
However, there are many other devices which can be damaged by overvoltage.

A crowbar circuit works by sensing a voltage that is above a certain threshold
and shorting out the power supply.
This causes a voltage drop in the rest of the circuit and current surge
through the power supply that will trip a circuit-breaker or blow a fuse.
The circuit must have a fuse or circuit-breaker, as without it the power
supply or the crowbar circuit will be damaged.
Crowbar circuits are so named because their activation is similar in effect
to dropping a crowbar across bus bars (heavy duty power supply lines).

A typical crowbar circuit is as follows:

[fig_1](crowbar.png)

This crowbar circuit has an 8V power supply, and triggers at around 10 V.
To change the power supply rating, the zener diode, ZD1, needs to be
changed to reflect the new trigger voltage.
It should be about 1 V higher than the nominal supply voltage.

- Fuse F1 is the fuse that blows if the current drawn by the circuit
  significantly exceeds 250 mA.
  This can be increased as needed, but make sure the thyristor Q1 has a
  higher current rating than the fuse.
  Also make sure the power supply can supply enough current to blow the
  fuse, as a current limited supply may fail to, and could overheat if
  the circuit is triggered.
- Capacitor C1's purpose is to reduce small, harmless, voltage spikes or
  noise which may trigger the circuit.
- ZD1 is the Zener diode which detects the overvoltage condition.
  At the threshhold voltage (here 9.1 V), it starts to conduct, and a
  further increase in supply voltage raises the voltage on R1 and Q1 gate.
- R1 is a pull-down resistor which holds the gate of thyristor Q1 low when
  ZD1 is not conducting.
- C2 is a snubber capacitor to prevent the thyristor being triggered by
  accident on being powered up.
  It must have a high enough value to filter transients, but low enough
  to avoid delaying the operation of Q1 too much.
- Q1 is the thyristor which provides a short-circuit between the power
  rails, blowing the fuse.
  When the gate voltage is pulled above its trigger voltage, typically in
  the 0.6 to 1 V range, it suddenly switches to conducting.
  The circuit trigger voltage is the sum of this and ZD1's theshhold
  voltage.
- SD1 is a Schottky diode to prevent kickback from the main circuit from
  triggering the crowbar circuit.
  Normal diodes can be used, but they have a larger voltage drop than
  Schottky diodes.
  This precaution is rarely needed.
