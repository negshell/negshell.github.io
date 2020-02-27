---
title: Molding and Casting
has_children: false
nav_order: 1
layout: default
---

# Molding and Casting for Soft Robotics
{: .no_toc }
Soft robots tend to rely on internal structures to operate. The infamous [PneuNets actuator](//softroboticstoolkit.com/book/pneunets-bending-actuator) used in many different soft robotic designs rely on a set of internal bellows that expand. Soft robotic sensors, especially those that operate using fluids like [salt water](//rombolabs.github.io/publications/preechayasomboon2019.pdf) or [EGaIn](//softroboticstoolkit.com/book/egain-sensors), rely on fluid channels that change shape and volume. The most common design element amongst these robotic components is usually silicone elastomer. Silicone rubber, unlike metal and most plastics, can stretch and deform by over 600% their original shape. Silicone rubber is also soft and compliant, like human tissue, so it is safer to be used around humans.

However, the main disadvantage of silicone rubber is that it is so compliant that traditional machining or manufacturing to achieve highly complex shapes is not feasible. This is why **molding and casting** silicone rubber is usually the preferred method for making soft robots.

Here, we present a brief overview and some guidelines on how to make soft robots with molding and casting. This guide also serves as a precursor to the concepts presented in the paper for those who are not familiar with soft robotic fabrication.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Fabrication Concepts
### Casting
**Casting** is the act of pouring or injecting a material in its liquid state into a cavity that resembles the final product. The liquid material will then solidify in the cavity or **mold** and then the mold is either removed or destroyed - leaving just the finished part. For soft robots, this liquid is typically the silicone rubber in its uncured state, which is usually a mixture of Part A and Part B of the silicone rubber.

### Molding
Molding and casting go hand-in-hand. Molding is the act of the making the cavity or mold where you would inject or pour the material to be casted. For the [special effects industry](//www.youtube.com/watch?v=DEVi0mEaJJQ), these molds are usually made by casting themselves, which usually involves casting around a "master" prop in a box to get a mold. For soft robotics purposes, we desire a more repeatable process, so most molds in soft robotics research is 3D printed or machined. With a highly-detailed mold, the liquid silicone rubber usually picks up all the fine details once casted so any external features can be simply designed into the 3D printed mold.

There are many types of molds depending on the technique used in casting that are used in the industry. The simplest mold is an open-top mold where the material can be simply poured into a "tub" that resembles the end product shape - this type of mold has limited use since one side of the finished product must be flat and the casted part must be able to be pulled out of the opening. Another type of mold is *injection molding*. Injection molding can be attributed to also plastics and metal injection molding, where high pressure and high temperature material is injected into a mold. For silicone rubbers, however, injection molding refers to injecting liquid silicone rubber into a closed mold, with only openings for the injection port and ventilation.

### Cores
External features can be created with molds, but what about internal features? In metal casting, for example to cast an engine, a **core** must be used to create the internal cavity for the pistons. Cores cannot be made out of solid material since they need to be removed later, so engine manufacturers usually use sand and binder to make temporary cores that are removed after the molten metal cools down and solidifies. For jewelers, lost-wax casting or investment casting is usually preferred. Wax can be 3D printed to make the core and later burned out after casting.

For soft robots, the core usually makes up the internal features of the components, such as a bladder or fluid channel. Wax can be used to make soft robot cores, but wax is prone to dimensional inaccuracies by shrinkage and is very fragile. Wax also requires being melted out, which depending on the wax can leave unwanted residue on the internal surface. Some internal features can be made by casting two or more separate pieces of the soft robotic component and later bond them together, but this requires multiple steps and the bonding can ultimately fail.

☆ Our paper introduces two new concepts to soft robotic fabrication: 3D printed [sacrificial](negshell-cores) and [structural cores](structural-cores) that are designed to be *left in* the soft robotic component rather than being removed after casting.

## Materials and Equipment
The following is a non-exhaustive list of materials and equipment for fabricating silicone-rubber based soft robots
### Silicone Rubber
Silicone rubber usually comes in two different chemistries: Platinum-Cure and Tin-Cure. Each have their own pros and cons. Silicone rubber is also generally categorized by how **soft** they are (the durometer) using the Shore scale. Starting from Shore 00-0 to Shore 00-40, which as soft as a gummy bear, to Shore 10A to Shore 80A which ranges from a rubber band to a hard eraser. Higher durometer in the Shore 30D to Shore 100D elastomers are typically urethane or plastic, not silicone.
##### Platinum-Cure Silicone
The platinum in Platinum-Cure silicone refers to the catalyst used to start the cure or hardening process. Platinum-cure silicone is known to be sensitive to any contaminants, which can inhibit curing. However, platinum-cure silicone has better overall mechanical properties and uncured shelf-life. Preparing platinum-cure silicone usually requires a 1-to-1 mixing ratio, making it less susceptible to measuring errors. Some platinum-cure silicone is also skin-safe and can be used for making molds for food. 3D printed molds used with platinum-cure silicone, especially resin-based printers, must be cleaned thoroughly before casting. Mold release agent should also be used in conjunction with casting and can help mitigate cure inhibition from any residual resin.

|Name|Durometer|Link|
|----|---------|----|
|Plat-Sil Gel 10|10A|[Polytek](//www.polytek.com/products/platsil-gel-10)|
|**Plat-Sil Gel 25**|25A|[Polytek](//www.polytek.com/products/platsil-gel-25)|
|Dragon Skin 30|30A|[Smooth-On](//www.smooth-on.com/products/dragon-skin-30/)|
|Smooth-Sil 945|45A|[Smooth-On](//www.smooth-on.com/products/smooth-sil-945/)|

The authors generally prefer **Plat-Sil Gel 25** due to its translucency, low viscosity, 1 hour demold time and biocompatibility. The same silicone rubber is used throughout the paper.

##### Tin-Cure Silicone
Tin-cure silicone or condensation cure silicone is a slightly less expensive alternative to platinum-cure silicone. Tin-cure silicone is less sensitive to contaminants, but comes at the cost of having worse mechanical properties. While platinum-cure silicone has neglible shrinkage, tin-cure silicone has a ~1% shrinkage, so designs must take into account this geometry change after curing. Tin-cure silicone typically has a mixing ratio of 1-to-10 of Part A and Part B, so measurements must be taken carefully. Despite the fact that tin-cure silicone is less susceptible to cure inhibition from contaminants, mold release agent should be used while casting.

##### Silicone Adhesives
Silicone rubber is notorious for not being able to readily adhere to any other material except for silica and glass. Tape, superglue, epoxy, etc. simply do not work. Even bonding silicone rubber to glass requires surface preparation using plasma. Silicone does not even bond to each other after 12-24 hours after casting - which means that casting on top of freshly cured silicone is possible, but not advisable.

The next best thing to bonding silicone together and silicone to other materials is silicone adhesive, such as Smooth-On Sil-Poxy and GE Silicone II†. These adhesives are good for sealing up tears and holes and can be used to bond silicone rubber to some plastics. An alternative to chemical bonding is mechanical bonding, as described [here](#mechanical-bonding).

|Name|Durometer|Link|
|----|---------|----|
|**Sil-Poxy**|40A|[Smooth-On](//www.smooth-on.com/products/sil-poxy/)|
|GE Silicone II†|80A?†|[GE](//www.gesealants.com/Products/GE-Silicone-2-Household-Glue)|

*†Using GE Silicone II is purely speculative from anecdotal evidence on the internet, it is more affordable but cures to a much higher durometer.*

### Release Agents
Using release agents is highly recommended for any silicone casting project. For lifecasts that is done on human skin, pretoleum jelly can be used. Melted pretoleum jelly can also be used as a substitute for release agents in a pinch. For silicone-based molds and 3D printed molds, use the release agent that is most compatible with the target casting material. 3D printed molds from FDM-style printers can have layer lines that end up becoming retaining structures making them difficult to demold, FDM molds should either be sanded smooth and sealed with a primer but is not absolutely necessary. Always check for compatibility with mold material and target material.

|Name|Mold Material|Link|
|----|-------------|----|
|**Pol-Ease 2500**|3D Printed (thoroughly cleaned), Silicone Rubber, and most materials|[Polytek](//www.polytek.com/products/pol-ease-2500-release-agent)|
|Ease Release|3D Printed (thoroughly cleaned), Silicone Rubber, and most materials|[Smooth-On](//www.smooth-on.com/product-line/ease-release/)|
|Pretoleum Jelly|Human Skin (Lifecasting)|Any drugstore|

*Please be careful around using release agents and work in a ventilated area with proper protection, as they are harmful!*

### Vacuum Degassing
To get the proper mechanical properties and cure from two-part silicone rubbers, the liquid silicone must be mixed thoroughly. This comes at the cost of introducing trapped gasses and bubbles to the mixture. Casting silicone rubber with bubbles will often result in weaker parts and bubbles can lead to ruptures and leaks in thin-walled structures. **Vacuum degassing** is usually the preferred method for removing gas bubbles trapped in mixed silicone rubber. This is done by placing the mixed silicone liquid (usually in a cup) into a vacuum pot (also known as catch-pots for infusing resins) and applying a -29 mmHg vacuum with at least 8 CFM of airflow using a vacuum pump. Rotary vane vacuum pumps can be costly, and alternatives such as vacuum hand-pumps can be used, but does not always work due to the high viscosity of liquid silicone rubber.

A simple trick for those who do not have access to expensive vacuum pumps is pouring the mixed silicone rubber into another container with a pencil lead-like thin stream. This will only remove large bubbles, but is better than not removing them altogether.

## Fabrication Guidelines
Here are guidelines to casting soft robotic parts using silicone rubber. Some of these are from experience - your mileage may vary!

### General Equipment
1. Silicone rubber
1. Plastic cups for mixing
1. Plastic or wooden stirring sticks - make sure there are no contaminants in the wood
1. Vacuum pump and vacuum chamber
1. Plastic syringe for injection molding
1. Disposable towels

### General Steps
(A ☆ denotes where our paper contributes to the overall process.)

1. **Prepare mold** by cleaning the mold thoroughly and applying a thin coat of release agent and letting it dry.
    1. ☆ **Prepare cores**: this can be either 3D printing our [cores](negshell-cores) or similar cores. And insert the cores into the mold.
    1. or go through a process as long as the upcoming steps just to cast the cores in wax and insert them into the mold.
    1. **Close and clamp the mold** parts shut tightly - silicone is highly viscous and can build up a lot of pressure.
1. **Mix silicone** by adding Part A and Part B to a plastic cup in amounts according to the manufacturer. Any pigments for coloring, or additives can be added too (for speeding up curing, slowing curing, lowering viscosity, increasing viscosity, etc.). If small amounts of silicone rubber is to be used, use an accurate digital scale (0.1 grams resolution or better). Generally, a mismatch of 0.5 grams is acceptable for 1-to-1 part platinum-cure silicone that totals < 50 grams after mixing. **Stir vigorously** if vacuum degassing later. **Use a cup that is at least three times taller than the mixed silicone** if vacuum degassing. Make sure to scrape all sides of the cup.
    1. **Using a dual-barrel syringe/cartridge kit with a mixing tip** is an alternative to mixing and pouring/injecting silicone rubber. Fill the cartridge with equal parts liquid silicone and skip to Step 6. The downside to this method is the large amount of waste created by the single use cartridges and mixing tips.
1. **Vacuum degas** by putting the cup in a vacuum chamber. Make sure the vacuum pump has vacuum oil. Make sure the ventilation cap is open. Make sure both valves are closed. Turn on pump. Open pump-side valve (usually red) and observe the vacuum reading. The silicone will bubble and foam up significantly. Depending on the viscosity of the silicone rubber, you might have to leave the vacuum running for a few minutes, take note of the *pour time* of your silicone rubber, as the liquid silicone will start to gel after this time. Turn off the pump then close the pump-side valve once the bubbles have subsided. Open the vent valve (usually blue) to release the vacuum and finally open the chamber to remove the cup.
1. **If not vacuum degassing** pour the mixed silicone into another cup with a thin pencil lead-like stream. This will remove larger bubbles but not completely.
1. **If injection molding** pour the mixed silicone into a syringe with a removed plunger, try to avoid creating bubbles by pouring with a thin stream. Carefully tilt the syringe tip up along with inserting the plunger in at an angle to let the trapped air travel up towards the tip and fully insert the plunger afterwards. Slowly push the plunger up to let the air out of the syringe.
1. **Inject/Pour silicone** into the mold. Depending on the geometry of the mold, this can be tricky to prevent trapping air. Tapping the mold can help remove some trapped air. The flow of silicone can by actively modulated while using the syringe. Using a clear material for the mold helps diagnose issues during injection/pouring. Make sure the mold has adequate ventilation, one inlet and one outlet is the absolute minimum. Having only one inlet will cause the silicone to build up pressure and not flow in the mold. If flashing (thin membranes that are created at the mold seams) is acceptable, then adding more pressure and letting the silicone flow out through the seams can help with small trapped bubbles near the seam.
1. **Release the casting** after the silicone has set. Usually the *demold time* given by the silicone manufacturer is enough time for the silicone rubber to be removed from the mold, but this can vary due to temperature and humidity. The mechanical properties at the demold time will not be ideal and usually the silicone rubber requires another 12 to 24 hours to fully cure to its maximum strength.
    1. ☆ **If you are using our casting method** you would simply continue on to the next step!
    1. **If you are using a traditional, solid core** this would be the first iteration through these steps. Some soft robotic designs requires casting multiple pieces on top of each other (overmolding), while others requires casting multiple pieces to be bonded together.
    1. **If you are using a wax-based core**, you would dissolve the wax using an oven and clean the remaining wax off. Water-soluble wax is a good alternative that only requires warm water to dissolve.
1. **Clean up** the usual mess created by silicone casting! If you spill *mixed* silicone rubber, just wait for it to cure and peel it off - trying to clean it up prior will lead to a larger mess. If you spill *unmixed* silicone rubber, use IPA and a disposable towel to clean.
1. **Seal** up any holes or seams using silicone adhesives. Silicone adhesives usually take 15 to 20 minutes to set. It is best to apply it on the freshly cured silicone (right after demolding).

### Eggshell Casting
Eggshell casting is a special method of casting almost exclusive to resin-based 3D printing where a thin-walled (0.5 - 0.8 mm) mold in the shape of surface of the final part is injected with silicone, and once cured the mold is broken apart. This method is useful for one-off castings of small, complex and intricate parts. Eggshell casting is one of the inspirations for our casting method. Formlabs has a tutorial for eggshell casting available [here](//3d.formlabs.com/rs/060-UIG-504/images/3D-Printing-Custom-Ear-Molds_formlabs-white-paper.pdf).

### Mechanical Bonding
As mentioned above, bonding silicone to other materials is difficult, if not impossible. 3D printed resins do not bond with silicone rubber even by using silicone adhesives like Sil-Poxy. The alternative is to use mechanical features in the part to *entrap* the silicone and retain it. This can be done by adding undercuts or overhangs to the bonding part. For example, with a raised plate with holes, the liquid silicone will flow around the plate and form a structure that "locks" the silicone in place. Retention features are also found in overmolded rubber on plastic or metal consumer products. [This paper](//www.sciencedirect.com/science/article/pii/S0264127519306926) explores several designs for creating these interlocking features.

## Other Resources
- [Smooth-On FAQ](//www.smooth-on.com/support/faq/)
- [Brick in the Yard Videos](//www.brickintheyard.com/pages/video-library)
- [Soft Robotics Toolkit](//softroboticstoolkit.com)
- [Tested.com Videos](//www.youtube.com/user/testedcom/featured)
