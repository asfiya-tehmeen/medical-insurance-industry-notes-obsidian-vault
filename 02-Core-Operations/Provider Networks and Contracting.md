# Provider Networks and Contracting

## What a network is
A set of doctors/hospitals that agreed to discounted rates in exchange for patient volume. Members pay less in-network.

## Lifecycle of a provider
1. **Recruitment** → 2. **Credentialing** (verify license, board certification, malpractice history, sanctions; NCQA standards; re-credential every 3 years) → 3. **Contracting** (rates, terms) → 4. **Loading** into systems (provider master) → 5. **Directory publication** → 6. **Monitoring** (quality, complaints, access) → 7. **Termination**.

## Provider data (very messy in real life!)
- Identifiers: **NPI** (individual 'Type 1', organization 'Type 2'), TIN, license, DEA, taxonomy codes (specialty).
- Locations, phone, panel status (accepting new patients), languages, hospital affiliations.
- Relationships: one doctor → many locations → many groups → many networks.
- Provider directory accuracy is legally required (No Surprises Act: verify every 90 days). Studies show a large share of directory entries are wrong, so **provider data management** is a big hiring area.
- Public source: NPPES NPI registry https://npiregistry.cms.hhs.gov

## Network adequacy
Regulators require enough doctors within time/distance standards for each specialty and county. Analysts use geo analytics (member addresses vs provider locations) to prove it. Medicare Advantage and Marketplace have formal standards.

## Contract components
Fee schedule (% of Medicare or flat rates), payment method (FFS/DRG/cap), stop-loss/outlier terms, quality bonuses, timely filing, appeal rights, termination notice.

## Pricing in claims
The claim's pricing engine looks up: provider → contract → fee schedule version effective on date of service → code → allowed amount. Wrong effective dates or missing contract rows are top causes of mispriced claims.

## Transparency rules
- **Hospital price transparency** & **Transparency in Coverage** (payers publish in-network negotiated rates as huge machine-readable JSON files). Great data-engineering practice: files are multi-GB. https://github.com/CMSgov/price-transparency-guide

## Value-based arrangements
ACOs, patient-centered medical homes, bundled payments. Require attribution logic (which members belong to which PCP) and quality and cost reporting.
