<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>AIRLAW</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; background: #fff; color: #000; }
    h1 { text-align: center; }
    .question-block { margin-bottom: 20px; padding: 10px; border-bottom: 1px solid #ccc; }
    .options-list { list-style: none; padding: 0; }
    .options-list li { margin: 5px 0; cursor: pointer; }
    .correct { color: green; font-weight: bold; }
    .incorrect { color: red; font-weight: bold; }
    .explanation { display: none; margin-top: 5px; font-style: italic; }
  </style>
</head>
<body>

<h1>NASA TEST PREP 1</h1>
<p>Click an answer to check if it's correct. All questions are scrollable below.</p>

<div id="questions"></div>

<script>
// Wait until page fully loads
window.onload = function() {

const questions = [
  {
    question: "1. Must the operator of an aircraft, in which dangerous goods are to be carried, provide the PIC with information concerning those goods?",
    options: [
      "a) The PIC must be advised of any dangerous goods, where the nature of those dangerous goods require special handling in flight, such as hold temperature control.",
      "b) Yes, The PIC must be advised that dangerous goods are being carried, and detailed information must be readily available in writing or by radio or other communication method as approved by the Director.",
      "c) Yes, it must be presented in writing on dedicated form.",
      "d) No, there is no requirement in CAR Part 92 for the PIC to be provided with any written information concerning dangerous goods, as long as they are packaged and labelled in accordance with the Technical Instructions."
    ],
    correct: 1,
    explanation: "The operator must advise the PIC that dangerous goods are being carried and ensure detailed information is readily available."
  },
  {
    question: "2. What are the requirements for entries into a technical logbook?",
    options: [
      "a) Entries must be made within 48 hours of the occurrence.",
      "b) Entries must be made before departure of the next flight.",
      "c) Entries must be made within 7 days of the occurrence.",
      "d) Entries are only needed after 10 flight hours."
    ],
    correct: 1,
    explanation: "Technical log entries must be made before departure of the next flight after the occurrence."
  },
  {
    question: "3. What should the pilot do if an ELT activates accidentally?",
    options: [
      "a) Switch off the unit and inform ATS as soon as practicable.",
      "b) Leave the unit on and continue flight.",
      "c) Switch off the unit and report the activation to the nearest ATS unit.",
      "d) Switch the unit off and record in the maintenance log."
    ],
    correct: 2,
    explanation: "The pilot must switch off the ELT and report to the nearest ATS unit."
  },
  {
    question: "4. What does the abbreviation VOR stand for?",
    options: [
      "a) VHF Omnidirectional Range",
      "b) Visual Observation Rules",
      "c) Variable Omnidirectional Radio",
      "d) Vertical Operations Regulations"
    ],
    correct: 0,
    explanation: "VOR stands for VHF Omnidirectional Range."
  },
  {
    question: "5. When departing from an unattended aerodrome, when should a standard departure broadcast be made?",
    options: [
      "a) After engine start.",
      "b) When lining up on the runway.",
      "c) After becoming airborne and setting heading.",
      "d) Before taxi."
    ],
    correct: 2,
    explanation: "The broadcast should be made after becoming airborne and setting heading."
},
{
    question: "6. What is the minimum fuel reserve required for turbine-powered aircraft operating under IFR in New Zealand?",
    options: [
      "a) 30 minutes at 1500 ft above destination.",
      "b) 45 minutes at 1500 ft above destination.",
      "c) 30 minutes at 5000 ft above destination.",
      "d) 45 minutes at 5000 ft above destination."
    ],
    correct: 1,
    explanation: "A 45-minute reserve at 1500 ft above the aerodrome is required."
},
{
    question: "7. In RVSM airspace above FL290, what is the standard vertical separation?",
    options: [
      "a) 500 ft",
      "b) 1000 ft",
      "c) 2000 ft",
      "d) 3000 ft"
    ],
    correct: 1,
    explanation: "In RVSM airspace above FL290, vertical separation is 1000 ft."
},
{
    question: "8. What is the correct emergency transponder code for unlawful interference (hijacking)?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7400"
    ],
    correct: 0,
    explanation: "7500 is the squawk code for unlawful interference."
},
{
    question: "9. What is the correct emergency transponder code for radio communication failure?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7800"
    ],
    correct: 1,
    explanation: "7600 is the squawk code for radio communication failure."
},
{
    question: "10. What is the correct emergency transponder code for a general emergency?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7800"
    ],
    correct: 2,
    explanation: "7700 is the squawk code for general emergency."
},
{
    question: "11. What must the PIC do after an emergency ELT activation?",
    options: [
      "a) Record it in the maintenance log only.",
      "b) Inform the nearest ATS unit as soon as possible.",
      "c) Continue flying without reporting.",
      "d) Wait until arrival to inform ATS."
    ],
    correct: 1,
    explanation: "The PIC must inform the nearest ATS unit as soon as possible."
},
{
    question: "12. Who is responsible for compliance with the Civil Aviation Rules during flight?",
    options: [
      "a) The operator.",
      "b) The flight engineer.",
      "c) The pilot-in-command.",
      "d) The flight dispatcher."
    ],
    correct: 2,
    explanation: "The PIC is responsible for compliance with the Civil Aviation Rules during flight."
},
{
    question: "13. Under what conditions can a visual approach be requested?",
    options: [
      "a) Only when requested by ATC.",
      "b) When weather conditions permit and approved by ATC.",
      "c) Only for VFR flights.",
      "d) Only during day operations."
    ],
    correct: 1,
    explanation: "A visual approach can be requested when weather permits, and ATC approves."
},
{
    question: "14. Minimum climb gradient for missed approach procedure unless otherwise specified?",
    options: [
      "a) 2.5%",
      "b) 3.3%",
      "c) 5%",
      "d) 10%"
    ],
    correct: 0,
    explanation: "Standard missed approach climb gradient is 2.5% unless otherwise specified."
},
{
    question: "15. Who is responsible for terminating an IFR flight plan at an unattended aerodrome?",
    options: [
      "a) The operator.",
      "b) The ATS unit.",
      "c) The PIC.",
      "d) Termination is automatic."
    ],
    correct: 2,
    explanation: "The PIC must manually terminate the IFR flight plan."
},
{
    question: "16. What is the minimum required separation between two RNP10 aircraft?",
    options: [
      "a) 50 NM",
      "b) 60 NM",
      "c) 100 NM",
      "d) 150 NM"
    ],
    correct: 2,
    explanation: "RNP10 aircraft require 100 NM separation longitudinally and laterally."
},
{
    question: "17. Under which rule can pilots deviate off track without prior clearance in Auckland Oceanic FIR?",
    options: [
      "a) Only for weather deviations with immediate safety concerns.",
      "b) Only if loss of communication.",
      "c) Always allowed.",
      "d) Only with ATC preapproval."
    ],
    correct: 0,
    explanation: "Immediate safety deviations for weather are allowed, with ATS advised ASAP."
},
{
    question: "18. What must be done if a pilot deviates for weather without prior clearance?",
    options: [
      "a) Report deviation after reaching destination.",
      "b) Immediately report the deviation to ATS.",
      "c) Land at the nearest aerodrome.",
      "d) Change squawk code to 7700."
    ],
    correct: 1,
    explanation: "Deviation must be reported to ATS immediately."
},
{
    question: "19. What is the maximum holding speed for Category C aircraft below 14,000 ft?",
    options: [
      "a) 170 KTAS",
      "b) 230 KTAS",
      "c) 240 KTAS",
      "d) 265 KTAS"
    ],
    correct: 2,
    explanation: "Category C maximum holding speed is 240 KTAS."
},
{
    question: "20. In RVSM airspace, which equipment is required?",
    options: [
      "a) Two independent altimeters, autopilot with altitude hold, and alerting system.",
      "b) One altimeter only.",
      "c) TCAS only.",
      "d) HF radio only."
    ],
    correct: 0,
    explanation: "Two independent altimeters, autopilot altitude hold, and alerting system are required."
},
{
    question: "21. When carrying dangerous goods, what document must be on board?",
    options: [
      "a) Flight Operations Manual.",
      "b) Dangerous Goods Transport Document.",
      "c) MEL (Minimum Equipment List).",
      "d) Maintenance Log."
    ],
    correct: 1,
    explanation: "Dangerous Goods Transport Document must be on board."
},
{
    question: "22. When can firearms be carried on board an air transport aircraft?",
    options: [
      "a) Only by passengers with special permission.",
      "b) Only by law enforcement officers authorized by the Director and PIC.",
      "c) Firearms are never allowed.",
      "d) Only in the cabin."
    ],
    correct: 1,
    explanation: "Only authorized law enforcement officers can carry firearms with Director and PIC approval."
},
{
    question: "23. What must the pilot ensure before operating into a volcanic hazard zone?",
    options: [
      "a) Visual conditions prevail.",
      "b) NOTAMs and SIGMETs reviewed and safe operation ensured.",
      "c) Weather forecast is good.",
      "d) Daylight operations only."
    ],
    correct: 1,
    explanation: "Pilot must review NOTAMs, SIGMETs and ensure safety."
},
{
    question: "24. When must a second alternate aerodrome be nominated?",
    options: [
      "a) When flight exceeds 3 hours.",
      "b) When destination and first alternate are marginal.",
      "c) When departing from international airports.",
      "d) Only for flights over mountains."
    ],
    correct: 1,
    explanation: "Two alternates are needed when destination and first alternate weather are marginal."
},
{
    question: "25. What must a pilot do after a communication failure under IFR in controlled airspace?",
    options: [
      "a) Land immediately.",
      "b) Squawk 7700 and return to departure aerodrome.",
      "c) Continue according to last clearance and flight plan.",
      "d) Orbit at last cleared altitude."
    ],
    correct: 2,
    explanation: "Continue based on last clearance or planned flight profile."
},
{
    question: "26. Under Part 91, within how long must a pilot record flight time in the logbook?",
    options: [
      "a) 24 hours after flight.",
      "b) 48 hours after flight.",
      "c) 7 days after flight.",
      "d) 30 days after flight."
    ],
    correct: 1,
    explanation: "Entries must be made within 48 hours after the flight."
},
{
    question: "27. When can a pilot commence a visual approach without ATC clearance?",
    options: [
      "a) Always in VMC.",
      "b) Never; always needs ATC clearance.",
      "c) Only if pilot sees the runway.",
      "d) When in uncontrolled airspace."
    ],
    correct: 1,
    explanation: "A visual approach always requires ATC clearance."
},
{
    question: "28. What is the meaning of squawk code 7700?",
    options: [
      "a) Communication failure.",
      "b) Hijacking.",
      "c) General emergency.",
      "d) Radar service termination."
    ],
    correct: 2,
    explanation: "7700 indicates a general emergency."
},
{
    question: "29. When must an ELT be tested?",
    options: [
      "a) Anytime during flight.",
      "b) Only in the first 5 minutes past the hour.",
      "c) Every 3 months.",
      "d) Only during maintenance."
    ],
    correct: 1,
    explanation: "Testing is allowed only in the first 5 minutes past the hour."
},
{
    question: "30. What separation standard applies to RNP4 operations?",
    options: [
      "a) 50 NM.",
      "b) 30 NM.",
      "c) 100 NM.",
      "d) 5 NM."
    ],
    correct: 1,
    explanation: "RNP4 operations use 30 NM separation standard."
},
{
    question: "31. Under what conditions can an aircraft operate into an aerodrome not listed in the AIP under Part 121?",
    options: [
      "a) Only if approved by the Director.",
      "b) Only during daylight hours.",
      "c) When specific conditions in the exposition are satisfied.",
      "d) Never allowed under Part 121."
    ],
    correct: 2,
    explanation: "An aerodrome not listed may be used if the conditions in the operator's exposition are satisfied."
},
{
    question: "32. What must be carried onboard when transporting dangerous goods by air?",
    options: [
      "a) Safety Management Manual.",
      "b) A Dangerous Goods Transport Document.",
      "c) Aircraft Maintenance Manual.",
      "d) Passenger briefing cards."
    ],
    correct: 1,
    explanation: "The Dangerous Goods Transport Document must be carried onboard."
},
{
    question: "33. What is the initial required action after noticing an ELT has activated accidentally during flight?",
    options: [
      "a) Land immediately.",
      "b) Report immediately to ATS.",
      "c) Record in technical log only.",
      "d) Turn it off after landing."
    ],
    correct: 1,
    explanation: "You must report activation to ATS as soon as practicable."
},
{
    question: "34. Minimum separation between aircraft above FL290 (non-RVSM equipped)?",
    options: [
      "a) 1000 ft.",
      "b) 2000 ft.",
      "c) 500 ft.",
      "d) 3000 ft."
    ],
    correct: 1,
    explanation: "Non-RVSM aircraft must maintain 2000 ft separation above FL290."
},
{
    question: "35. What is the standard holding speed limit below 14,000 ft?",
    options: [
      "a) 230 knots.",
      "b) 240 knots.",
      "c) 265 knots.",
      "d) 170 knots."
    ],
    correct: 1,
    explanation: "Standard maximum holding speed below 14,000ft is 240 KTAS."
},
{
    question: "36. What is the VHF emergency frequency for aircraft communications?",
    options: [
      "a) 121.5 MHz.",
      "b) 122.8 MHz.",
      "c) 243.0 MHz.",
      "d) 406 MHz."
    ],
    correct: 0,
    explanation: "The VHF emergency frequency is 121.5 MHz."
},
{
    question: "37. Which aircraft require RVSM approval to operate between FL290 and FL410 inclusive?",
    options: [
      "a) All aircraft.",
      "b) Aircraft intending to operate above FL290.",
      "c) Only jet aircraft.",
      "d) Only aircraft over 5700kg MTOW."
    ],
    correct: 1,
    explanation: "Aircraft operating between FL290�FL410 require RVSM approval."
},
{
    question: "38. In the event of a hijacking (unlawful interference), which squawk code should be set?",
    options: [
      "a) 7500.",
      "b) 7600.",
      "c) 7700.",
      "d) 1200."
    ],
    correct: 0,
    explanation: "Squawk 7500 for unlawful interference."
},
{
    question: "39. What is the minimum vertical separation standard applied in New Zealand's RVSM airspace?",
    options: [
      "a) 2000 ft.",
      "b) 1000 ft.",
      "c) 500 ft.",
      "d) 2500 ft."
    ],
    correct: 1,
    explanation: "RVSM reduces separation to 1000 ft vertically between FL290�FL410."
},
{
    question: "40. How soon must a technical defect be entered into the aircraft's technical log?",
    options: [
      "a) Immediately after discovery.",
      "b) Before the next flight.",
      "c) After landing at destination.",
      "d) Within 7 days."
    ],
    correct: 1,
    explanation: "Entries must be made before departure of the next flight."
},
{
    question: "41. What action must be taken if an ELT activates accidentally while on the ground?",
    options: [
      "a) Turn it off and advise ATS immediately.",
      "b) No action is needed.",
      "c) Record it in the maintenance log only.",
      "d) Wait for maintenance personnel."
    ],
    correct: 0,
    explanation: "Switch off the ELT and advise ATS immediately."
},
{
    question: "42. Which of the following best describes the definition of controlled airspace?",
    options: [
      "a) Airspace where ATC services are not provided.",
      "b) Airspace where ATC services are provided to IFR flights only.",
      "c) Airspace where ATC services are provided to IFR and VFR flights.",
      "d) Any airspace at or above 10,000 ft."
    ],
    correct: 2,
    explanation: "Controlled airspace provides ATC services to both IFR and VFR flights."
},
{
    question: "43. What frequency is used for ELT transmissions?",
    options: [
      "a) 121.5 MHz and 406 MHz.",
      "b) 122.8 MHz.",
      "c) 243.0 MHz only.",
      "d) 1090 MHz."
    ],
    correct: 0,
    explanation: "ELTs transmit on 121.5 MHz and 406 MHz."
},
{
    question: "44. How often must transponders be inspected and tested?",
    options: [
      "a) Every 6 months.",
      "b) Every 12 months.",
      "c) Every 24 months.",
      "d) Every 36 months."
    ],
    correct: 2,
    explanation: "Transponders must be inspected and tested every 24 months."
},
{
    question: "45. In what situation would a pilot squawk code 7700?",
    options: [
      "a) Hijacking.",
      "b) Communication failure.",
      "c) General emergency.",
      "d) Transponder failure."
    ],
    correct: 2,
    explanation: "7700 is the code for general emergency."
},
{
    question: "46. When operating in RVSM airspace, what equipment must be carried?",
    options: [
      "a) Two primary altimeters, autopilot with altitude hold, and alerting system.",
      "b) Only GPS equipment.",
      "c) HF radio only.",
 	  "d) TCAS only."
    ],
    correct: 0,
    explanation: "RVSM requires two independent altimeters, autopilot, and altitude alerting."
},
{
    question: "47. Minimum climb gradient for departure unless otherwise specified?",
    options: [
      "a) 2.5%.",
      "b) 3.3%.",
      "c) 5%.",
      "d) 10%."
    ],
    correct: 0,
    explanation: "Standard departure climb gradient is 2.5%."
},
{
    question: "48. What does the abbreviation RNP stand for?",
    options: [
      "a) Required Navigation Performance.",
      "b) Random Navigation Procedure.",
      "c) Required Navigational Path.",
      "d) Range Navigation Performance."
    ],
    correct: 0,
    explanation: "RNP = Required Navigation Performance."
},
{
    question: "49. What is the meaning of the squawk code 7600?",
    options: [
      "a) Hijacking.",
      "b) General emergency.",
      "c) Radio communication failure.",
      "d) Radar failure."
    ],
    correct: 2,
    explanation: "7600 is the squawk for radio communication failure."
},
{
    question: "50. Minimum equipment for RVSM operation includes:",
    options: [
      "a) HF radios only.",
      "b) Two independent altimeters and autopilot with altitude hold function.",
      "c) VHF radios and TCAS only.",
      "d) Single transponder and altimeter."
    ],
    correct: 1,
    explanation: "RVSM minimum equipment includes two independent altimeters and autopilot with altitude hold."
},
{
    question: "51. When operating under IFR in controlled airspace and a communications failure occurs, the pilot must:",
    options: [
      "a) Land at nearest aerodrome.",
      "b) Continue according to last assigned clearance.",
      "c) Orbit overhead last reporting point.",
      "d) Squawk 7500."
    ],
    correct: 1,
    explanation: "Continue flight in accordance with last assigned clearance or flight plan."
},
{
    question: "52. What squawk code must be set during unlawful interference (hijacking)?",
    options: [
      "a) 7500.",
      "b) 7600.",
      "c) 7700.",
      "d) 7400."
    ],
    correct: 0,
    explanation: "7500 is the squawk for unlawful interference."
},
{
    question: "53. What is the meaning of VOR?",
    options: [
      "a) Visual Operation Radio.",
      "b) Variable Omnidirectional Receiver.",
      "c) VHF Omnidirectional Range.",
      "d) Visual Orientation Radar."
    ],
    correct: 2,
    explanation: "VOR stands for VHF Omnidirectional Range."
},
{
    question: "54. How long does an operator have to report an ELT activation after landing if it occurred accidentally?",
    options: [
      "a) Immediately.",
      "b) Within 24 hours.",
      "c) Within 7 days.",
      "d) Within 48 hours."
    ],
    correct: 0,
    explanation: "Must be reported immediately after landing."
},
{
    question: "55. Which frequency is monitored for emergency communications?",
    options: [
      "a) 122.8 MHz.",
      "b) 243.0 MHz.",
      "c) 121.5 MHz.",
      "d) 406 MHz."
    ],
    correct: 2,
    explanation: "121.5 MHz is the VHF emergency frequency."
},
{
    question: "56. When is a Dangerous Goods Transport Document required?",
    options: [
      "a) Only for international flights.",
      "b) Whenever dangerous goods are carried by air.",
      "c) Only for cargo aircraft.",
      "d) Only with passengers."
    ],
    correct: 1,
    explanation: "Required whenever dangerous goods are transported by air."
},
{
    question: "57. Under Civil Aviation Rules, who is ultimately responsible for the safety of the aircraft during flight?",
    options: [
      "a) The operator.",
      "b) The flight engineer.",
      "c) The flight dispatcher.",
      "d) The pilot-in-command."
    ],
    correct: 3,
    explanation: "The PIC is responsible for the safety of the aircraft and operation."
},
{
    question: "58. What action must be taken following a deviation due to weather without prior clearance in Auckland Oceanic FIR?",
    options: [
      "a) Continue deviation and notify ATS when convenient.",
      "b) Report deviation to ATS immediately.",
      "c) Land at nearest aerodrome.",
      "d) Set squawk code 7700."
    ],
    correct: 1,
    explanation: "Deviation must be reported immediately to ATS."
},
{
    question: "59. What does RNP stand for?",
    options: [
      "a) Random Navigational Procedure.",
      "b) Required Navigational Performance.",
      "c) Required Navigational Procedure.",
      "d) Random Navigational Performance."
    ],
    correct: 1,
    explanation: "RNP stands for Required Navigational Performance."
},
{
    question: "60. What equipment must be operational to fly in RVSM airspace?",
    options: [
      "a) TCAS and HF radio.",
      "b) Two independent altitude measurement systems, autopilot, and altitude alert system.",
      "c) VOR receiver and Mode C transponder.",
      "d) RNAV and ILS only."
    ],
    correct: 1,
    explanation: "RVSM requires two independent altitude systems, autopilot with altitude hold, and alerting system."
},
{
    question: "61. In the event of communication failure under IFR, what transponder code should the pilot set?",
    options: [
      "a) 7500.",
      "b) 7600.",
      "c) 7700.",
      "d) 7000."
    ],
    correct: 1,
    explanation: "Squawk 7600 for communications failure."
},
{
    question: "62. When must a second alternate be listed in the IFR flight plan?",
    options: [
      "a) When no alternate is required.",
      "b) When weather at destination and first alternate is marginal.",
      "c) When MEL limitations require it.",
      "d) When destination is beyond 100 NM."
    ],
    correct: 1,
    explanation: "Two alternates required if both destination and first alternate weather are marginal."
},
{
    question: "63. What does the squawk code 7500 indicate?",
    options: [
      "a) Emergency.",
      "b) Communication failure.",
      "c) Unlawful interference (hijacking).",
      "d) Loss of navigation capability."
    ],
    correct: 2,
    explanation: "7500 indicates unlawful interference."
},
{
    question: "64. What is the standard minimum fuel reserve for IFR turbine-powered flights?",
    options: [
      "a) 15 minutes at 1500ft above destination.",
      "b) 30 minutes at 5000ft above destination.",
      "c) 45 minutes at 1500ft above destination.",
      "d) 1 hour at 5000ft above destination."
    ],
    correct: 2,
    explanation: "45 minutes reserve at 1500 ft above the destination."
},
{
    question: "65. What does the squawk code 7700 indicate?",
    options: [
      "a) Unlawful interference.",
      "b) General emergency.",
      "c) Communications failure.",
      "d) System error."
    ],
    correct: 1,
    explanation: "7700 indicates general emergency."
},
{
    question: "66. When are pilots required to terminate IFR flight plans themselves?",
    options: [
      "a) Always, at any aerodrome.",
      "b) Only at controlled aerodromes.",
      "c) At unattended aerodromes.",
      "d) Never; ATC does it automatically."
    ],
    correct: 2,
    explanation: "Pilots must terminate IFR flight plans themselves at unattended aerodromes."
},
{
    question: "67. If a visual approach is requested, what must the pilot be able to maintain?",
    options: [
      "a) Sight of terrain only.",
      "b) Sight of aerodrome or preceding aircraft.",
      "c) Radar contact with ATS.",
      "d) Two-way communication with other traffic."
    ],
    correct: 1,
    explanation: "Pilot must maintain visual reference with terrain or aerodrome."
},
{
    question: "68. A pilot experiencing lost communications under IFR must continue:",
    options: [
      "a) At current heading and speed indefinitely.",
      "b) According to last assigned clearance and then as filed.",
      "c) Land immediately at nearest aerodrome.",
      "d) Set squawk 7500."
    ],
    correct: 1,
    explanation: "Continue per last clearance then according to filed flight plan."
},
{
    question: "69. When must entries in a pilot�s logbook be made?",
    options: [
      "a) Within 7 days of the flight.",
      "b) Before the end of the month.",
      "c) Within 48 hours after the flight.",
      "d) Whenever convenient."
    ],
    correct: 2,
    explanation: "Pilot logbook entries must be made within 48 hours."
},
{
    question: "70. Which squawk code represents radio communication failure?",
    options: [
      "a) 7500.",
      "b) 7600.",
      "c) 7700.",
      "d) 7000."
    ],
    correct: 1,
    explanation: "7600 is the code for communication failure."
},
{
    question: "71. Which squawk code indicates a general emergency?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7000"
    ],
    correct: 2,
    explanation: "7700 is the code for a general emergency."
},
{
    question: "72. When can a pilot commence a visual approach in controlled airspace?",
    options: [
      "a) Only when cleared by ATC.",
      "b) When VMC exists, regardless of ATC.",
      "c) Only when below 1000ft AGL.",
      "d) Only during day time."
    ],
    correct: 0,
    explanation: "Pilot must receive ATC clearance before commencing a visual approach."
},
{
    question: "73. The operator must ensure that the PIC is provided with information concerning dangerous goods:",
    options: [
      "a) Only if the goods are not labeled.",
      "b) Only if requested by the PIC.",
      "c) Always, and the information must be readily available.",
      "d) Only on international flights."
    ],
    correct: 2,
    explanation: "The operator must ensure the PIC has full information about dangerous goods on board."
},
{
    question: "74. In the event of a communication failure under IFR, the pilot should:",
    options: [
      "a) Land immediately at the nearest airport.",
      "b) Continue flight according to last clearance and the flight plan.",
      "c) Divert to an alternate aerodrome.",
      "d) Squawk 7500."
    ],
    correct: 1,
    explanation: "Pilot must continue according to last clearance and the filed flight plan."
},
{
    question: "75. ELT testing should only be done:",
    options: [
      "a) Anytime.",
      "b) Once a month.",
      "c) Only during maintenance.",
      "d) Within the first 5 minutes of any hour."
    ],
    correct: 3,
    explanation: "ELT testing is permitted within the first 5 minutes of any hour."
},
{
    question: "76. For a turbine powered aircraft under IFR, fuel carried must allow for:",
    options: [
      "a) Flight to destination, then 45 min at 5000ft.",
      "b) Flight to destination, alternate, and 30 min reserve.",
      "c) Flight to destination, alternate, and 45 min reserve at 1500ft.",
      "d) Flight to destination only."
    ],
    correct: 2,
    explanation: "Turbine aircraft must carry fuel to destination, alternate, and 45 min reserve at 1500ft."
},
{
    question: "77. How often must a transponder be tested under CAR Part 91?",
    options: [
      "a) Every 6 months.",
      "b) Every 12 months.",
      "c) Every 24 months.",
      "d) Every 36 months."
    ],
    correct: 2,
    explanation: "Transponders must be tested every 24 months."
},
{
    question: "78. Which code must be set if a pilot experiences unlawful interference?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7000"
    ],
    correct: 0,
    explanation: "7500 is the code for unlawful interference (hijacking)."
},
{
    question: "79. If an IFR flight experiences a total radio failure, what squawk code must be set?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7000"
    ],
    correct: 1,
    explanation: "7600 is the code for communication failure."
},
{
    question: "80. If deviating for weather without clearance in Auckland Oceanic FIR, the pilot must:",
    options: [
      "a) Squawk 7700 and divert.",
      "b) Continue deviation and notify ATS as soon as possible.",
      "c) Stay on track until clearance is received.",
      "d) Turn back immediately."
    ],
    correct: 1,
    explanation: "Deviation must be reported to ATS immediately if prior clearance isn't possible."
},
{
    question: "81. What equipment must a pilot ensure is operational before entering RVSM airspace?",
    options: [
      "a) Two primary altitude measurement systems, autopilot with altitude hold, and altitude alerting system.",
      "b) One primary altimeter only.",
      "c) HF radio and TCAS.",
      "d) GPS and radar altimeter."
    ],
    correct: 0,
    explanation: "RVSM operations require two independent altitude systems, autopilot with altitude hold, and an altitude alert system."
},
{
    question: "82. When is a second alternate aerodrome required?",
    options: [
      "a) Always for domestic flights.",
      "b) When destination and first alternate are forecast below landing minima.",
      "c) When distance exceeds 100NM.",
      "d) When MEL items are deferred."
    ],
    correct: 1,
    explanation: "Second alternate required when both destination and first alternate weather is marginal."
},
{
    question: "83. Who has responsibility for compliance with the Civil Aviation Act during the flight?",
    options: [
      "a) The aircraft engineer.",
      "b) The flight dispatcher.",
      "c) The operator.",
      "d) The pilot-in-command."
    ],
    correct: 3,
    explanation: "The PIC is responsible for compliance with the Civil Aviation Act during flight."
},
{
    question: "84. What action must be taken after a Dangerous Goods incident occurs?",
    options: [
      "a) Inform the operator after landing.",
      "b) Record in the aircraft maintenance log.",
      "c) Immediately report to the appropriate authority.",
      "d) Notify ATC only."
    ],
    correct: 2,
    explanation: "Dangerous Goods incidents must be immediately reported to appropriate authorities."
},
{
    question: "85. When is a Dangerous Goods Transport Document NOT required?",
    options: [
      "a) For cargo aircraft only.",
      "b) For consumer commodities meeting specific conditions.",
      "c) For domestic flights.",
      "d) Always required."
    ],
    correct: 1,
    explanation: "For certain low-risk consumer commodities, a Transport Document is not required."
},
{
    question: "86. What is the maximum time limit for a pilot to complete a flight log entry under Part 61?",
    options: [
      "a) 24 hours.",
      "b) 48 hours.",
      "c) 7 days.",
      "d) 30 days."
    ],
    correct: 1,
    explanation: "Pilot must complete log entry within 48 hours after flight."
},
{
    question: "87. In the case of radio communication failure under IFR, what should the pilot do?",
    options: [
      "a) Squawk 7700.",
      "b) Continue according to last clearance and flight plan.",
      "c) Land at the nearest aerodrome.",
      "d) Circle at last cleared altitude."
    ],
    correct: 1,
    explanation: "Pilot must continue according to last clearance and flight plan."
},
{
    question: "88. What action is required if an ELT is accidentally activated?",
    options: [
      "a) Do nothing; it will deactivate itself.",
      "b) Switch it off and report to nearest ATS unit immediately.",
      "c) Only inform maintenance after landing.",
      "d) Wait for 30 minutes to confirm."
    ],
    correct: 1,
    explanation: "ELT activation must be reported immediately to ATS."
},
{
    question: "89. What equipment is mandatory for an aircraft operating under RNP4 requirements?",
    options: [
      "a) Two FMCs and one IRS.",
      "b) RNAV system capable of meeting RNP4 standards.",
      "c) HF radios only.",
      "d) VOR/DME receiver."
    ],
    correct: 1,
    explanation: "An RNAV system capable of meeting RNP4 standards is required."
},
{
    question: "90. What does the abbreviation 'RVSM' stand for?",
    options: [
      "a) Required Vertical Separation Minimum.",
      "b) Reduced Vertical Separation Minimum.",
      "c) Required VFR Separation Minimum.",
      "d) Reduced VOR Separation Minimum."
    ],
    correct: 1,
    explanation: "RVSM stands for Reduced Vertical Separation Minimum."
},
{
    question: "91. Under Civil Aviation Rules, when can firearms be carried aboard an aircraft?",
    options: [
      "a) Never.",
      "b) Only with Director and PIC approval for authorized personnel.",
      "c) Always, if unloaded.",
      "d) Only for flights under 1 hour."
    ],
    correct: 1,
    explanation: "Only authorized persons with Director and PIC approval may carry firearms."
},
{
    question: "92. What does the squawk code 7600 indicate?",
    options: [
      "a) Hijacking.",
      "b) General emergency.",
      "c) Radio communication failure.",
      "d) Navigation equipment failure."
    ],
    correct: 2,
    explanation: "7600 indicates radio communication failure."
},
{
    question: "93. During a missed approach, what minimum climb gradient is assumed unless otherwise specified?",
    options: [
      "a) 2.5%",
      "b) 3.3%",
      "c) 5%",
      "d) 6%"
    ],
    correct: 0,
    explanation: "Standard missed approach assumes 2.5% climb gradient."
},
{
    question: "94. After what period must a VFR flight plan be terminated if no arrival report is received?",
    options: [
      "a) 30 minutes.",
      "b) 60 minutes.",
      "c) 90 minutes.",
      "d) 15 minutes."
    ],
    correct: 1,
    explanation: "After 60 minutes, a SAR phase is initiated if no arrival report."
},
{
    question: "95. What squawk code represents unlawful interference?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7000"
    ],
    correct: 0,
    explanation: "7500 represents unlawful interference."
},
{
    question: "96. What is required for operation in oceanic RNP10 airspace?",
    options: [
      "a) Two independent long-range navigation systems.",
      "b) One RNAV system.",
      "c) HF radio only.",
      "d) Visual navigation equipment."
    ],
    correct: 0,
    explanation: "Two independent long-range navigation systems required for RNP10."
},
{
    question: "97. Who is responsible for ensuring compliance with dangerous goods carriage requirements?",
    options: [
      "a) Air traffic control.",
      "b) The aircraft engineer.",
      "c) The operator.",
      "d) The passenger."
    ],
    correct: 2,
    explanation: "The operator is responsible for dangerous goods compliance."
},
{
    question: "98. What should a pilot do after an ELT test confirms accidental activation?",
    options: [
      "a) Ignore it.",
      "b) Record it only in the maintenance log.",
      "c) Immediately notify ATS.",
      "d) Deactivate the transponder."
    ],
    correct: 2,
    explanation: "Pilot must immediately notify ATS after accidental ELT activation."
},
{
    question: "99. Under RVSM, what is the vertical separation between aircraft at FL330?",
    options: [
      "a) 1000 ft.",
      "b) 2000 ft.",
      "c) 500 ft.",
      "d) 3000 ft."
    ],
    correct: 0,
    explanation: "Vertical separation under RVSM is 1000 ft at FL330."
},
{
    question: "100. Which transponder code is used for general emergency?",
    options: [
      "a) 7500",
      "b) 7600",
      "c) 7700",
      "d) 7000"
    ],
    correct: 2,
    explanation: "7700 is used for general emergency situations."
},
{
    question: "101. Who is responsible for compliance with Civil Aviation Rules during the conduct of a flight?",
    options: [
      "a) The flight dispatcher.",
      "b) The pilot-in-command.",
      "c) The operator.",
      "d) The air traffic controller."
    ],
    correct: 1,
    explanation: "The pilot-in-command (PIC) is responsible for compliance during flight."
},
{
    question: "102. In case of emergency and deviation from rules, when must the PIC report it?",
    options: [
      "a) Only if requested.",
      "b) Immediately after flight.",
      "c) Within 7 days.",
      "d) Not required if no damage."
    ],
    correct: 1,
    explanation: "Emergency deviations must be reported to the Director as soon as practicable after the flight."
},
{
    question: "103. Under what condition can an aircraft deviate from ATC clearance without prior approval in oceanic airspace?",
    options: [
      "a) Only in case of loss of communication.",
      "b) Only if requested by another aircraft.",
      "c) Only if necessary for weather avoidance and safety.",
      "d) Deviations are not permitted under any condition."
    ],
    correct: 2,
    explanation: "Deviation for immediate safety (such as weather avoidance) is permitted without prior clearance."
},
{
    question: "104. How is an unintentional ELT activation treated?",
    options: [
      "a) No action needed if in controlled airspace.",
      "b) Must be reported to ATS immediately.",
      "c) Record it only in aircraft maintenance log.",
      "d) Ignore if less than 5 minutes."
    ],
    correct: 1,
    explanation: "An unintentional ELT activation must be reported to the nearest ATS unit immediately."
},
{
    question: "105. What must a pilot do if he/she squawks 7500 by mistake?",
    options: [
      "a) Immediately squawk 7600.",
      "b) Immediately squawk 7700.",
      "c) Continue squawking 7500 and inform ATC by voice.",
      "d) Turn off the transponder."
    ],
    correct: 2,
    explanation: "If 7500 is transmitted by mistake, continue squawking and inform ATC by voice if possible."
}
  // (AND CONTINUE LIKE THIS FOR ALL YOUR 105 QUESTIONS)
];

// Now build the page
const container = document.getElementById('questions');

questions.forEach((q, index) => {
  const block = document.createElement('div');
  block.className = 'question-block';
  
  const qText = document.createElement('p');
  qText.innerHTML = `<strong>Q${index + 1}:</strong> ${q.question}`;
  block.appendChild(qText);
  
  const list = document.createElement('ul');
  list.className = 'options-list';
  
  const explanation = document.createElement('p');
  explanation.className = 'explanation';
  explanation.textContent = `Explanation: ${q.explanation}`;
  
  q.options.forEach((opt, i) => {
    const li = document.createElement('li');
    li.textContent = opt;
    li.onclick = function() {
      if (li.classList.contains('correct') || li.classList.contains('incorrect')) return;
      if (i === q.correct) {
        li.classList.add('correct');
      } else {
        li.classList.add('incorrect');
      }
      explanation.style.display = 'block';
    };
    list.appendChild(li);
  });
  
  block.appendChild(list);
  block.appendChild(explanation);
  container.appendChild(block);
});

}; // End of window.onload
</script>

</body>
</html>
