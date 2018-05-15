# Entity Types

## Health System
Healthbase defines health systems as a legal corporation owning at least one hospital and at least one other facility of any type.  Health systems can own other health systems, making the distinction between a 'Top Level Parent' and an 'Intermediary' health system.  
Health System affiliations are derived from IRS filings (for non-profit health systems), SEC filings (publicly listed systems), State regulatory filings (State/County/City owned health systems), or secondary research from Healthbase analysts.  


## Physician Group
Physician groups are legal corporations made of groups of physicians, either multi-specialty or single-specialty.  Healthbase represents only the legal corporation of a physician group and shows all physicians who bill directly to that group, work at an office with an NPI owned by that group, are listed as a member of the group by the CMS physician compare file, or have been approved to submit Medicare part A/B claims through the group in the CMS PECOS file.  
While physician groups are legally distinct corporations, they may be owned or tightly affiliated to health systems.  Healthbase identifies ownership by showing a score of '100' between a health system and a hospital.  Healthbase shows other types of relationships with a score of less than 100.  In those cases, claims data indicates that patient activity is occurring in a hospital or other institution owned by a health system but being billed directly to a physician group for the professional portion of the claim.  This indicates a direct contractual relationship between the health system for the group to provide physician services at the location.


## Ambulatory Surgical Center
Ambulatory surgery centers, or ASCs, are facilities focused on providing outpatient surgical care, including diagnostic and preventative procedures.  ASCs provide more efficient care by reducing the need for costly inpatient hospital stays and often narrow their focus to a single therapeutic area.  ASCs can be owned by a single hospital, part of a broader health system, or owned by ASC chains focused exclusively on providing outpatient surgical care.


## Hospital
Healthbase uses the CMS provider of service file to define hospitals.  All hospitals are approved to accept patients for inpatient stays, however there are many categories of hospitals.  The typical example is a general acute care hospital, but specialty hospitals exist for rehabilitation, mental health care, transplants, or long term care.  
Hospitals often have many different NPIs associated with different departments at the site.  Healthbase aligns all the different NPIs attached to hospital to enable data integration and analytics at the single entity level, helping our customers with a variety of business questions.


## Accountable Care Organization

### Definition
Accountable Care Organizations, or ACOs, are best described as contractual relationships between payers and providers.  There are a wide array of different ACO types, but the critical distinction is that providers signed onto an ACO have either upside or downside risk associated with payments for care delivered over the year.  The payments that are subject to that risk are usually still paid over the year in a fee for service type model, but those payments are then aggregated and compared to the contractual benchmarks.  Those contractual rules are set during negotiation, and define exactly which types of patients will be included in the ACO calculations at the end of each reporting period.  A second piece of the initial negotiation determines what benchmarks the provider will need to achieve financially and clinically to receive payment. 
Because the payment calculations are made at the end of the year based patient attribution rules, a patient does not necessarily know whether they are in an ACO.  For example, a contract might define the relevant patient population as everyone covered by a payer who received at least 90% of their medical/prescription services from a signatory of the ACO contract.  The patient is not directly limited or forced to stay within the network defined by the ACO, but relevant clinical and financial targets would be set by the portion of all patients who have met the criteria by the end of the year.  This aspect differentiates ACOs from other types of shared risk programs like come HMO contracts, since patients are not limited to a particular network and the shared savings or return of payment is only analyzed at the end of each reporting period.  
Financial goals are usually determined by risk adjusted rates of payments that can shift based on the number of patients who qualify for the ACO. Usually these targets are set by historical data the payer possesses based on what they have paid for care at the facility in the past.  
Clinical goals are an important piece of ACO contracts as well.  To prevent providers from meeting financial goals by cutting services or ignoring patient needs, payers and providers negotiate on which clinical metrics will be analyzed during the reporting period and exactly what standard will be required to qualify for payment.  
        
        
### Types of ACOs
ACOs can be signed by all manner of payers and providers.  CMS runs several programs that are either explicitly general ACOs (Pioneer Model, Medicare Shared Savings Program, Next Generation) or cover narrow therapeutic areas (End Stage Renal Disease Program, Oncology Care Model).  Many state Medicaid offices also created their own versions of ACO programs for those populations.  Some private insurers have followed CMS's lead and become heavily involved with ACO contracting across their commercial, managed Medicare, and managed Medicaid businesses.
On the provider side, again ACO contracting partners can be quite diverse.  Single health systems can sign ACOs, often leveraging large technology investments to ensure consistent tracking of patient outcomes and physician behavior to stay on track with ACO goals.  Those health systems can also open their ACO contract to include outside providers, with legal allowance to assist those providers with technological investments to conform to reporting standards. In other cases, collections of individual providers or smaller physician groups can band together to collectively sign ACO contracts with payers.  Two big challenges for collections of smaller providers is raising capital for the required technology and enforcing behavioral changes required to meet goals.  These types of ACOs will often elect a central organizer to help coordinate behavior, reviewing the data generated by the new standardized reporting platform to encourage all providers to make choices leading to better and more cost efficient outcomes.


## Practitioner
Healthbase has an expansive definition of health care practitioner.  Any individual with an NPI who meets the following criteria is included within Healthbase:
  * Individual has submitted medical claims in the past 6 months represented in DRG's proprietary claims database (covers approx. 70% of the Commercial, Managed Medicare, and Managed Medicaid activity in the US).
  * Individual has submitted Medicare part A or B claims to CMS in the past year.
  * Individual is approved to have Medicare part A or B claims submitted on their behalf by another organization per the CMS PECOS file.  


Typically this means that Healthbase tracks not only MDs/DOs, but also nurse practitioners, physician assistants, and other care givers approved by private insurers to be reimbursed for care like chiropractors or rehab specialists.
