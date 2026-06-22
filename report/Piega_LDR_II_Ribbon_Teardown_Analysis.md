# Reverse-Engineering a Piega LDR II Ribbon

### A teardown analysis of a Piega LDR II linear ribbon tweeter, from the P 4 XL MK II

> **Provenance.** Driver salvaged from a pair of **Piega P 4 XL MK II** floorstanders;  a 3-way Swiss bass-reflex design of the early 2000s, rated 89 dB / 4 Ω;  acquired second-hand via Ricardo. The tweeter is Piega's own **LDR II** (Linear Drive Ribbon, generation II). "DC / direct-coupled" is used in this writeup as a working description of the driver's no-transformer operation, not as Piega's designation.

---

## 1. What this driver actually is

Piega is a Swiss high-end loudspeaker manufacturer whose signature technology is the "ribbon" driver. The unit examined here is the **LDR II** (Linear Drive Ribbon, generation II);  the ribbon tweeter from the P 4 XL MK II, where it serves as the high-frequency driver in a 3-way system.

The first thing worth clearing up is the name. Despite being marketed as a *ribbon*, this is technically a **planar-magnetic driver**, and the distinction matters:

- A **true ribbon** is a single strip of conductive foil suspended in a magnetic field. The foil is *both* the conductor and the moving surface. Because a bare foil strip has almost no resistance (typically 0.1–0.5 Ω), it cannot be connected to an amplifier directly;  it needs a step-up transformer to match it to the amp.
- A **planar-magnetic** driver uses a thin plastic film (here, Kapton) with a separate conductive trace pattern printed or etched onto it. The film is the moving surface; the trace is the "voice coil." Because the trace can be made long and thin, its resistance is sane (this one measures **2.8 Ω**), so it can be driven **directly** with no transformer.

Throughout this writeup the driver is described as *direct-coupled* ("DC");  a working description of that no-transformer property, not Piega's own designation (their name for it is the LDR II). The 2.8 Ω measurement confirms it: this is a driver you can hang straight off a normal amplifier through a passive crossover.

![Diaphragm conductor side above its magnet plate](../figures/diaphragm-back.png)
*Figure 1;  Diaphragm (conductor side) above its magnet plate.*

---

## 2. The operating principle

Every driver here obeys the same piece of physics, the **motor law**:

> Force = B × I × L

A conductor carrying current **I**, of length **L**, sitting in a magnetic field of strength **B**, feels a force at right angles to both. Reverse the current and the force reverses;  feed it an audio signal and the surface pushes and pulls the air in step with the music.

Two terms are worth keeping in mind for later:

- **BL** ("force factor") is the product of field strength and conductor length in the field. It sets how much force you get per amp of signal;  in plain terms, the driver's **efficiency**. Lose BL and the driver goes quiet.
- **Br** ("remanence") is the field strength a permanent magnet produces. It is the **B** in the equation above, so anything that weakens the magnets directly weakens the driver.

The advantage of the planar layout is that the driving force is applied **across the whole membrane at once**, wherever the traces run;  not injected at a single point and propagated outward, the way a conventional cone is driven through its voice coil. Combined with an extremely light membrane, this gives the fast, clean transient response these drivers are prized for. It also makes them unusually tolerant of localised damage, since no single point is doing all the work.

---

## 3. Construction at a glance

From the listening side inward, the driver is a simple sandwich:

| Layer | Material | Approx. dimension |
|---|---|---|
| Front plate | Steel, with a rectangular window | 2 mm thick; opening ≈ 25.8 × 41.8 mm |
| Spacer / gasket | Hard rubber | ≈ 1.6 mm (sets the air gap) |
| Diaphragm | Aluminised Kapton on a fibreboard frame | conductor a few microns thick |
| Air gap |;  | ≈ 1.6 mm to the magnet faces |
| Magnets | 3 × neodymium bars | each ≈ 50 × 10 × 5 mm, ≈ 5 mm apart |
| Rear yoke | Soft steel plate joining all three magnets | ≈ 5 mm |
| Damping | Felt | thin |

The full internal cavity is roughly **81 × 41 mm**, but the **active radiating area is only 25.8 × 41.8 mm**;  a point we return to in the design notes, because the difference is mostly "dead" area.

A striking feature is how *little* adhesive the whole thing uses. The inter-magnet gaps and the spaces above and below the magnets are filled with **removable felt** (acoustic damping, not structural potting). There are really only **two glued joints in the entire driver**: the magnets bonded to the steel yoke, and the Kapton bonded to its frame. Everything else is mechanical assembly held together by four screws. The diaphragm's carrier frame is a **translucent fibreboard that looks like FR-grade (glass-fibre/epoxy) laminate**;  a common workshop material, not a proprietary moulding.

---

## 4. The motor (magnet system)

Three neodymium bar magnets sit *behind* the diaphragm;  none on the sides, none on the front. This is a **single-ended** magnet system. A soft-steel **yoke** behind the magnets ties them together magnetically and provides a return path for the field; the steel front plate completes the magnetic circuit on the other side and adds shielding and structure.

The three bars are arranged in **alternating polarity;  N–S–N**. This was confirmed without any specialist tools: presenting the same face of a spare ferrite magnet to each bar in turn, the two outer bars *attracted* it while the middle bar *repelled* it. Alternating polarity is what makes the motor work. Between two oppositely-poled bars, the magnetic field runs **horizontally across the gap**, parallel to the diaphragm;  and it is that in-plane field that produces useful (perpendicular) force on the conductors running over the gaps. Over the centre of each bar the field points straight up, which does **not** drive the membrane outward; only the gap regions do real work. The serpentine/spiral trace pattern is laid out so the current direction reverses from one gap to the next, matching the alternating field so all the forces add.

Single-ended is the right choice *for a tweeter*. The membrane barely moves, so the fact that the field weakens with distance from the magnets (which would normally cause distortion as the diaphragm swings in and out of a stronger/weaker field) simply doesn't have room to express itself. The reasons to add magnets on *both* sides are covered in the design notes.

*Figure 2;  Alternating N–S–N bar magnets and rear plate. (Add R5 close-up; the motor is also visible in Figure 1.)*

---

## 5. The diaphragm and "voice coil"

The diaphragm is **aluminised Kapton**;  the familiar amber polyimide film, with an etched aluminium conductor on one face. (Piega quote a conductor around 7 µm thick and a moving mass of roughly 7 milligrams, which is consistent with what's here.) Aluminium is chosen over copper deliberately: it is about a third of the density, so the membrane stays light, which is what buys the high-frequency extension and speed.

The film is mounted **conductor-side-out**;  the aluminium traces face the front plate, and the bare Kapton faces the magnets. This orientation turns out to be quietly important, as Section 7 explains.

The conductor itself is **two concentric rectangular spirals wired in parallel**, terminating in four contact pads that collapse to two terminals, with two fine lead wires routed to the rear. Wiring the two spirals in parallel **halves both the resistance and the inductance** versus a single long spiral. Lower inductance is exactly what you want at the top of the audio band, so for a tweeter this is a feature, not a compromise;  it keeps the driver fast and keeps the impedance flat and easy to drive.

Measured terminal resistance is **2.8 Ω**, confirmed both at the external terminals and directly at the diaphragm pads.

One inefficiency stands out. The **active** trace area is only 25.8 × 41.8 mm, but the trace pattern occupies the full ≈ 81 × 41 mm footprint. The extra area is **bus routing**;  the wiring that carries current to and from the active loops;  and it sits *on the moving membrane*, where it adds series resistance and moving mass while producing no sound. This is a design point worth improving on (Section 8).

![Diaphragm front, trace pattern backlit](../figures/diaphragm-front.png)
*Figure 3;  Diaphragm front (radiating face), trace pattern backlit.*

---

## 6. The pleating: corrugation as modal control

The membrane is **corrugated**;  finely pleated in one direction, much finer than the corrugation on a conventional ribbon. (An earlier impression that it was textured with a two-dimensional bump field turned out to be a moiré illusion from product video; it is a simple, fine transverse pleat.)

What's clever is that the pleating is **not uniform**. The pattern runs roughly **four corrugated traces, then one flat column, repeating**. This is deliberate compliance shaping:

- The **corrugated bands** stiffen the membrane against unwanted bending and help break up standing waves.
- The **flat columns** act as built-in **hinge lines**;  controlled places where the membrane is *allowed* to flex.

Corrugating the entire surface would over-stiffen it and fight the very motion you are trying to drive. Selectively pleating it lets the designer decide *where* the membrane is rigid and *where* it is compliant;  in other words, it tunes the **modal behaviour** (the pattern of resonances) directly into the geometry of the diaphragm. It is a notably more sophisticated approach than "corrugate it for stiffness," and the pleat period very likely maps onto the magnet bar-and-gap spacing;  stiff over the active zones, compliant in between.

---

## 7. The dummy traces (and why the failure wasn't worse)

Down the centre of the active area sit roughly **eight conductor strips that are not wired to anything**;  they carry no current. At first glance this looks like a mistake. It isn't.

These strips lie **directly over the centre of the middle magnet**, exactly where the field points straight up and can produce no useful driving force. So there is no point wiring them. But they aren't left as bare Kapton either, and that is the deliberate part. Aluminised film and bare film have **different mass and different stiffness**. A bare stripe down the middle of a driven membrane would be lighter and floppier than its surroundings;  it would lag behind, flap, and seed its own resonance right in the radiating area. The **dummy strips keep the mass and stiffness uniform** so the whole membrane moves as one piece.

There is almost certainly a **manufacturing reason** riding along too. In an etching process, areas with uniform pattern density etch at a uniform rate; a large blank area next to fine traces etches differently ("etch loading") and throws off the dimensions of the real traces nearby. Filling the dead zone with dummy features keeps the etch even;  the same reasoning behind copper-balancing fill on a printed circuit board. The strips serve acoustics and fabrication at once.

The conductor-side-out mounting (Section 5) is what kept the eventual failure from being catastrophic: the fragile aluminium traces face *away* from the magnets, so when the motor failed, it was the tough Kapton side;  not the conductor;  that took the damage.

---

## 8. Why it measured wrong: oxide jacking

The driver had a strange frequency response and elevated distortion in part of its band. The cause, found on disassembly, is a textbook but rarely-witnessed failure mode: **oxide jacking** of the neodymium magnets.

Neodymium (NdFeB) magnets corrode readily, so they are plated;  typically nickel-copper-nickel. Over decades, moisture eventually works under the plating and the magnet begins to corrode from the **grain boundaries inward**. Corrosion products take up **more volume** than the metal they replace (the same mechanism as rust jacking, where rusting steel cracks concrete). That expansion levers the plating off the magnet face as a hard, buckled **crust**.

This single mechanism explains every symptom, along two completely independent lines:

1. **Mechanical.** The crust grew **taller than the 1.6 mm air gap** and pressed against the back of the diaphragm, partially clamping it and stopping it moving freely. *Result:* distorted frequency response and localised distortion;  worst opposite the centre magnet, which was the most corroded. The driver felt strangely "over-tensioned" by hand; it was actually jammed.
2. **Magnetic.** The same corrosion ate into the working faces of the magnets and converted magnet material into magnetically **dead oxide**. *Result:* the field **B** in the gap collapsed, **BL** fell with it, and the driver lost sensitivity;  which matches the recollection that these "90 dB-ish" drivers played audibly quiet.

Two unrelated measurements;  distortion and low output;  pointing at the same root cause is what turns the diagnosis from a hypothesis into a conclusion. By the end, the corrosion had gone clean through: the bars had separated along their own corroded planes top and bottom, so the magnets lifted away with almost no force, leaving the *adhesive* perfectly intact. The driver didn't fail at any joint a designer chose; it failed inside the magnet metal itself, after the better part of two decades of slow, passive corrosion.

*Figure 4;  Lifted plating crust on the magnet faces, most severe on the centre bar. (Add R5 close-up; visible in Figure 1.)*

---

## 9. Design implications;  what I would change

Reverse-engineering this driver surfaces several improvements worth carrying into an original planar design:

**Keep the dead wiring off the moving membrane.** The biggest inefficiency here is the bus routing printed on the diaphragm, which adds resistance and moving mass for zero output, and leaves only about a third of the area doing real work. Routing the inter-loop and bus connections on a **static external frame** instead maximises the active area and minimises both moving mass and dead resistance.

**Protect the membrane with a grille.** A planar diaphragm is a sub-10-micron tensioned film;  almost as fragile as a true ribbon despite not being one. A protective grille or mesh on a finished product is not a cosmetic nicety; it is mechanical necessity. (This is also a genuine durability argument for **AMT** drivers further down a product roadmap: their folded, self-supporting membranes are inherently more robust.)

**Radius the diaphragm-to-frame transition.** Where the film bends over the edge of its frame, the original uses a **sharp corner**. A sharp edge is a **stress concentrator**;  it focuses mechanical load onto a line, so the film is most likely to tear there under tension or shock. A **radiused (filleted) edge** spreads that stress over an arc and dramatically raises the tear threshold. It is the same principle that puts a fillet on every well-designed bracket.

**Use push-pull only where excursion demands it.** Single-ended (magnets one side) is correct for a tweeter, where the membrane barely moves. For a **midrange** with real excursion, a **push-pull** arrangement (magnets on both sides) keeps BL constant across the stroke and cuts distortion. Piega's coaxial models reportedly do exactly this;  adding **thin magnets on the opposite face** of the midrange diaphragm to symmetrise the field without shadowing the radiating area. The lesson: match motor complexity to how far the diaphragm actually travels.

**Prefer aluminium for the conductor.** Copper is easier to source and etch, but it is roughly three times denser than aluminium. For a high-frequency driver, where low moving mass *is* the performance, aluminium is worth the extra fabrication effort.

**Design for corrosion from day one.** The only long-term failure mode here was magnet corrosion, and standard plating clearly isn't permanent. More robust protection;  epoxy- or parylene-coated magnets, or sealing the finished motor;  extends service life. One specific caution: never use **acetoxy-cure ("vinegar smell") silicone** anywhere near neodymium magnets. It off-gasses acetic acid as it cures and actively accelerates the exact corrosion seen here; use neutral/oxime-cure silicone or epoxy instead.

---

## 10. A note on impedance and amplifier loading

A 2.8 Ω DC resistance looks alarmingly low;  that's woofer territory, and amplifiers dislike low-impedance woofers. But it is perfectly fine **here**, for reasons specific to what this driver is:

- A planar is a **nearly resistive** load. With very little inductance (helped further by the parallel spirals), the impedance stays close to 2.8 Ω and **flat, with almost no phase angle**. What actually stresses an amplifier is low impedance *combined with a large phase swing*;  that's when high current and high voltage overlap in the output devices. A benign, resistor-like 2.8 Ω is an easy load.
- Behind a **high-pass crossover**, the tweeter only draws current at high frequencies, where the energy in music is already low. A 2.8 Ω *woofer* pulling current across the whole bass range is a hard load; a 2.8 Ω *tweeter* sipping current above a few kHz is not.

The practical takeaway is that the common "3.5 Ω minimum" rule of thumb is really about woofers and full-range drivers. For a high-passed, nearly-resistive planar tweeter, a sub-3.5 Ω resistance is fine on a solid-state amplifier, and a small series resistor can flatten the load further and add margin if desired. (A tube amplifier on an 8 Ω tap cares more about the mismatch; a chip or solid-state amp does not.)

---

## 11. Summary

Stripped to its essentials, the Piega LDR II is:

- a **planar-magnetic** driver (marketed as a ribbon), **direct-coupled** at 2.8 Ω;
- driven by a **single-ended, alternating-polarity (N–S–N)** array of three neodymium bars on a steel yoke, with a steel front plate completing the magnetic circuit;
- using an **aluminised-Kapton** membrane carrying **two parallel spirals**, **selectively pleated** for modal control, with **dummy strips** over the dead centre for uniform mass and even etching;
- assembled almost entirely **mechanically**, with felt damping and just two glued joints, on an **FR-type fibreboard** frame.

What's notable is that **every one of those subsystems is an accessible material or process**;  etched aluminium on polyimide, mild-steel yokes, off-the-shelf neodymium bars, fibreboard frames, mechanical assembly. The real achievement on display is not any single exotic trick, but the **consistency** required to reproduce fine-pitch etched membranes, precise pleating and accurate magnet alignment **repeatably, at low production volume**. The hard part was never making one good diaphragm;  it was making the next twelve identical to it.

The failure, finally, is almost a compliment to the design: after roughly two decades of passive service, the only thing that gave out was the slow, inevitable corrosion of the magnets' plating;  the last component to go, long after foam surrounds and electrolytic capacitors would have killed an ordinary driver.
