# Entity Types

## Health System

Healthbase defines health systems as a legal corporation owning at least one hospital and at least one other facility of any type. Health systems can own other health systems, making the distinction between a 'Top Level Parent' and an 'Intermediary' health system.

Health System affiliations are derived from IRS filings \(for non-profit health systems\), SEC filings \(publicly listed systems\), State regulatory filings \(State/County/City owned health systems\), or secondary research from Healthbase analysts.

## Physician Group

Physician groups are legal corporations made of groups of physicians, either multi-specialty or single-specialty. Healthbase represents only the legal corporation of a physician group and shows all physicians who bill directly to that group, work at an office with an NPI owned by that group, are listed as a member of the group by the CMS physician compare file, or have been approved to submit Medicare part A/B claims through the group in the CMS PECOS file.

While physician groups are legally distinct corporations, they may be owned or tightly affiliated to health systems. Healthbase identifies ownership by showing a score of '100' between a health system and a hospital. Healthbase shows other types of relationships with a score of less than 100. In those cases, claims data indicates that patient activity is occurring in a hospital or other institution owned by a health system but being billed directly to a physician group for the professional portion of the claim. This indicates a direct contractual relationship between the health system for the group to provide physician services at the location.

## Ambulatory Surgical Center

Ambulatory surgery centers, or ASCs, are facilities focused on providing outpatient surgical care, including diagnostic and preventative procedures. ASCs provide more efficient care by reducing the need for costly inpatient hospital stays and often narrow their focus to a single therapeutic area.

ASCs can be owned by a single hospital, part of a broader health system, or owned by ASC chains focused exclusively on providing outpatient surgical care.

## Hospital

Healthbase uses the CMS provider of service file to define hospitals. All hospitals are approved to accept patients for inpatient stays, however there are many categories of hospitals. The typical example is a general acute care hospital, but specialty hospitals exist for rehabilitation, mental health care, transplants, or long term care.

Hospitals often have many different NPIs associated with different departments at the site. Healthbase aligns all the different NPIs attached to hospital to enable data integration and analytics at the single entity level, helping our customers with a variety of business questions.

## Accountable Care Organization

### Definition

Accountable Care Organizations, or ACOs, are best described as contractual relationships between payers and providers. There are a wide array of different ACO types, but the critical distinction is that providers signed onto an ACO have either upside or downside risk associated with payments for care delivered over the year. The payments that are subject to that risk are usually still paid over the year in a fee for service type model, but those payments are then aggregated and compared to the contractual benchmarks. Those contractual rules are set during negotiation, and define exactly which types of patients will be included in the ACO calculations at the end of each reporting period. A second piece of the initial negotiation determines what benchmarks the provider will need to achieve financially and clinically to receive payment.

Because the payment calculations are made at the end of the year based patient attribution rules, a patient does not necessarily know whether they are in an ACO. For example, a contract might define the relevant patient population as everyone covered by a payer who received at least 90% of their medical/prescription services from a signatory of the ACO contract. The patient is not directly limited or forced to stay within the network defined by the ACO, but relevant clinical and financial targets would be set by the portion of all patients who have met the criteria by the end of the year. This aspect differentiates ACOs from other types of shared risk programs like some HMO contracts, since patients are not limited to a particular network and the shared savings or return of payment is only analyzed at the end of each reporting period.

Financial goals are usually determined by risk adjusted rates of payments that can shift based on the number of patients who qualify for the ACO. Usually these targets are set by historical data the payer possesses based on what they have paid for care at the facility in the past.

Clinical goals are an important piece of ACO contracts as well. To prevent providers from meeting financial goals by cutting services or ignoring patient needs, payers and providers negotiate on which clinical metrics will be analyzed during the reporting period and exactly what standard will be required to qualify for payment.

### Types of ACOs

ACOs can be signed by all manner of payers and providers. CMS runs several programs that are either explicitly general ACOs \(Pioneer Model, Medicare Shared Savings Program, Next Generation\) or cover narrow therapeutic areas \(End Stage Renal Disease Program, Oncology Care Model\). Many state Medicaid offices also created their own versions of ACO programs for those populations. Some private insurers have followed CMS's lead and become heavily involved with ACO contracting across their commercial, managed Medicare, and managed Medicaid businesses.

On the provider side, again ACO contracting partners can be quite diverse. Single health systems can sign ACOs, often leveraging large technology investments to ensure consistent tracking of patient outcomes and physician behavior to stay on track with ACO goals. Those health systems can also open their ACO contract to include outside providers, with legal allowance to assist those providers with technological investments to conform to reporting standards. In other cases, collections of individual providers or smaller physician groups can band together to collectively sign ACO contracts with payers.

Two big challenges for collections of smaller providers is raising capital for the required technology and enforcing behavioral changes required to meet goals. These types of ACOs will often elect a central organizer to help coordinate behavior, reviewing the data generated by the new standardized reporting platform to encourage all providers to make choices leading to better and more cost efficient outcomes.

## Practitioner

Healthbase has an expansive definition of health care practitioner. Any individual with an NPI who meets the following criteria is included within Healthbase:

* Individual has submitted medical claims in the past 6 months represented in DRG's proprietary claims database \(covers approx. 70% of the Commercial, Managed Medicare, and Managed Medicaid activity in the US\).
* Individual has submitted Medicare part A or B claims to CMS in the past year.
* Individual is approved to have Medicare part A or B claims submitted on their behalf by another organization per the CMS PECOS file.  

Typically this means that Healthbase tracks not only MDs/DOs, but also nurse practitioners, physician assistants, and other care givers approved by private insurers to be reimbursed for care like chiropractors or rehab specialists.

## **Healthcare Group**

Healthcare groups are derived from CMS PECOS database from which we can know which entities are grouped together and share a common owner. But these PECOS/healthcare groups are not legal entities.

Healthcare group usually acts as a health system in the absence of ownership based affiliations.

## **Nursing Home**

Nursing home is a term that includes both skilled nursing facilities and nursing facilities. Skilled nursing facilities \(SNF\) are those that participate in both Medicare and Medicaid. Nursing facilities \(NF\) are those that participate in Medicaid only.

Nursing homes primarily engage in providing residents skilled nursing care and related services for residents who require medical or nursing care and rehabilitation services for the rehabilitation of injured, disabled, or sick individuals.

## Home Health

Home health care is a wide range of health care services that can be given in your home for an illness or injury. Home health care is usually less expensive, more convenient, and just as effective as care you get in a hospital or skilled nursing facility \(SNF\).

## Hospice

Hospice is specialized type of care for those facing a life-limiting illness, their families and their caregivers. It addresses the patient’s physical, emotional, social and spiritual needs.

Hospice care takes place in the patient’s home or in a home-like setting and concentrates on managing a patient’s pain and other symptoms so that the patient may live as comfortable as possible and make the most of the time that remains.

## Dialysis Facility

Kidney failure, medically referred to as end-stage renal disease \(ESRD\), often requires patients to undergo dialysis, either in their own home or at a dialysis facility.

Dialysis is necessary to remove waste products from the blood. To see whether dialysis is removing enough waste products, a dialysis facility should periodically measure how effective dialysis treatments have been in removing that waste.

## Federally Qualified Health Center

Federally Qualified Health Centers are community-based health care providers that receive funds from the HRSA Health Center Program to provide primary care services in underserved areas. They must meet a stringent set of requirements, including providing care on a sliding fee scale based on ability to pay and operating under a governing board that includes patients.

Federally Qualified Health Centers may be Community Health Centers, Migrant Health Centers, Health Care for the Homeless, and Health Centers for Residents of Public Housing.

## Intermediate Care Facility

Intermediate Care Facilities for individuals with Intellectual disability \(ICF/ID\) is an optional Medicaid benefit that enables states to provide comprehensive and individualized health care and rehabilitation services to individuals to promote their functional status and independence. Although it is an optional benefit, all states offer it, if only as an alternative to home and community-based services waivers for individuals at the ICF/ID level of care.

## Mental Health Center

An entity that Provides outpatient services, including specialized outpatient services for children, the elderly, individuals who are chronically mentally ill, and residents of its mental health service area who have been discharged from inpatient treatment at a mental health facility;

Provides 24-hour-a-day emergency care services;

Provides day treatment or other partial hospitalization services, or psychosocial rehabilitation services;

Provides screening for patients being considered for admission to State mental health facilities to determine the appropriateness of this admission; and

Meets applicable licensing or certification requirements for CMHCs in the State in which it is located.

## Organ Procurement Organization \(OPO\)

It is a non-profit organization that is responsible for the evaluation and procurement of deceased-donor organs for organ transplantation. 

All these OPOs are members of the Organ Procurement and Transplantation Network \(OPTN\), a federally mandated network created by and overseen by the United Network for Organ Sharing \(UNOS\). 

The individual OPOs represent the front-line of organ procurement, having direct contact with the hospital and the family of the recently deceased donor. Once the OPO receives the consent of the decedent's family, it works with UNOS to identify the best candidates for the available organs, and coordinates with the surgical team for each organ recipient.

## Outpatient Physical Therapy Services

It means the physical therapy services provided by the public health agencies, service providers, and clinic rehabilitation agencies to outpatients.

The main aim of outpatient physical therapy services is to help people to restore movement and function, relieve pain, and prevent further injury. It provides evaluation and treatment of numerous physical conditions for all age groups.

Outpatient physical therapy services is provided to people with musculoskeletal disorders such as back and neck strains or knee injuries, neurological deficits such as stroke or cerebral palsy, and skin disorders such as wounds, burns or diabetic foot ulcers.

## Comprehensive Outpatient Rehabilitation Facility

It is medical facility that provides outpatient diagnostic, therapeutic, and restorative services for the rehabilitation of your injury, disability, or illness. CORF care is commonly known as outpatient rehabilitation care. CORFs must provide medical care, therapy, and certain social or psychological services.

## Portable X-Ray Suppliers

They provide diagnostic imaging services at patients’ locations—most often residences, including private homes and group living facilities, such as nursing homes—rather than in a traditional clinical setting, such as a doctor’s office or hospital. 

Medicare pays portable suppliers separately for up to four components of the service: transporting the equipment to the beneficiary’s location, setting it up for use, administering the test, and interpreting the results.

## Psychiatric Residential Treatment Facility

A psychiatric residential treatment facility \(PRTF\) is a non-hospital facility offering intensive inpatient services to people who have various mental health issues and are under the age of 21. All services are provided by a physician. The goal of a PRTF is to stabilize or improve a child’s condition until therapeutic services are no longer needed.

They can administer inpatient care to teenagers and children whose mental health needs are not met in other settings, such as school, home, or individual therapy. They provide a structured therapeutic environment, safe but intensive treatment, plans based around the child's needs, and treatment for chronic issues.

## Rural Health Clinic

It is a clinic located in a rural, medically under-served area in the United States that has a separate reimbursement structure from the standard medical office under the Medicare and Medicaid programs. The RHC program increases access to health care in rural areas by 

* creating special reimbursement mechanisms that allow clinicians to practice in rural, under-served areas
* increasing utilization of physician assistants \(PA\) and nurse practitioners \(NP\)

  









           





























\*\*\*\*

