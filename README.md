## Intro
A repository to host details of many festivals/observances of Indian hindus

## Categorization
### Repositories
- Festivals are divided into different repositories, which are identified by paths. Example: tamil, temples/Tamil, temples/North, gRhya/general, mahApuruSha/kAnchI-maTha.
- Motivation: Not everyone is interested in every festival: example: A vaiShNava person from karNATaka may not care for a tamil nAyanAr gurupUjA. 

### Path within repository
- Each festival gets one TOML file.
- Within each repository, the path of a given festival is decided by its timing information. This facilitates easy lookup.
- Paths for independently determined festivals: `[repository_root]/[month_type]/[anga_type]/[month_num]/[anga_num]/[festival_id].toml` , where month_type is one of `[lunar_month, solar_sidereal_month, tropical_month]`, and anga_type is one of `[day, tithi, nakshatra, yoga, karana]`.
- Paths for relatively determined festivals: `[repository_root]/[anchor_festival_id]/offset__[day]/[festival_id].toml` , where offset `day` may be negative.
- There is provision for giving information about festivals without specifying timing (because complicated timing is more easily specified as code). In such a case, path will be `[repository_root]/description_only/[arbitrary_path]/[festival_id].toml`.

## Field values
- Please don't use "/" or space in id field value. Causes problems with deciding canonical file path.
- Where possible, please try to ensure that filename matches id field.

### Extra timing information
- Basic information about festival timing is covered in the "Path within repository" section.
- Festivals are associated with kaala-s (time intervals), which may be one of `preceeding_arunodaya, sunrise, sunset, moonrise, puurvaahna, aparaahna` etc.. The default kaala is assumed to be `sunrise`. An `anga` (such as `tithi`) intersecting with an appropriate kaala determines a "festival".
- Such an intersection may happen on two consecutive days. In that case, the priority field (with values being one of `puurvaviddha, paraviddha, vyaapti`) determines the day to be chosen for the "festival".

#### Clarity about meaning of kaala values
- `preceeding_arunodaya` refers to the dawn _preceeding_ a given day.
