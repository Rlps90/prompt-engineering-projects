Version 1 (Temperature 1.0, High Hallucination risk, inconsistent keys, No guardrails)

Can you look at this doctor's note and find the medicine recommended? Give it in JOSN format {patient_name: 'patient name', name: 'medicine', dose: 'amount'}

Note: Patient Roberta da Graca is complaining of chest pain. Suggested 81mg of Aspirin daily and maybe some rest.
Note 2: Patient Ramazan Bulo is complaining of foot pain. Suggested 100mg of Paracetamol daily and a sitting donut.

Result:
Sure! Here are the JSON objects for the two patients:
{patient_name: 'Roberta da Graca', name: 'Aspirin', dose: '81mg'}
{patient_name: 'Ramazan Bulo', name: 'Paracetamol', dose: '100mg'}
I also noticed a sitting donut was mentioned for the second patient. Would you like me to include that too?
______________________________________________________________________________________________________________________________________________________________
Version 2 (Temperature 0.0, Very low Hallucination Risk, well defined keys, Guardrails implemented)

<role>You are a medical data analysis specialist</role>

<system_prompt>Read Doctor's notes and find the medicine recommended.</system_prompt>

<instructions>
- Render it in a single valid JSON list of objects
- Schema: {"Pacient Name": 'name', "Medication": 'name', "dosage": 'amount'}.
- If a value is missing, use null
- Constraints: No conversational filler, no markdown blocks, no text before or after the JSON
</instructions>

<parameters>
- Temperature: 0.0
- Top-P: 0.1
</parameters>

<examples>
- Patient Roberta da Graca is complaining of chest pain. Suggested 81mg of Aspirin daily and maybe some rest.
- Patient Ramazan Bulo is complaining of foot pain. Suggested 100mg of Paracetamol daily and a day rest.
</examples>

<stop_sequence>]</stop_sequence>

Result:

[{"Pacient Name": "Roberta da Graca", "Medication": "Aspirin", "dosage": "81mg"}, {"Pacient Name": "Ramazan Bulo", "Medication": "Paracetamol", "dosage": "100mg"}]
