---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Audience Manager mapping field
topic: overview
---

# Audience Manager mapping fields

The tables below contain the mappings between the fields in Adobe Audience Manager data (Realtime, Onboarded, and Profile data) and their corresponding XDM fields.

Please see the [XDM field dictionary](../../../../xdm/schema/field-dictionary.md) for more information on each XDM Field.

## Realtime data

Type: Realtime data

| Realtime Data Field | XDM Field |
| --- | --- |
| `requestIds[]` | `ExperienceEvent.identityMap["ECID"]` |
| `requestIds[]` | `ExperienceEvent.endUserIds` - *Only for namespaces present in endUserIds and only first value.* |
| `primaryDeviceId` | `ExperienceEvent.identityMap["CORE"]` |
| `primaryDeviceId` | ExperienceEvent.endUserIds - *Only for namespaces present in endUserIds and only first value.* |
| `trait[] `| `ExperienceEvent.segmentMemberships["AAMTraits"]` |
| `segments[]` | `ExperienceEvent.segmentMemberships["AAMSegments"]` |
| `mergeRules[]` |`ExperienceEvent.profileStitch[]` |
| `timestamps` | `ExperienceEvent.timeStamp` |
| `deviceMetadata` | `ExperienceEvent.device` <ul><li>primaryHardwareType → type</li><li>manufacturer → manufacturer</li><li>marketingName → model</li><li>modelNumber → model</li></ul>|
| `location` | `ExperienceEvent.placeContext.geo` <ul><li>d_country → countryCode</li><li>d_state → stateProvince</li><li>d_city → city</li><li>d_postal → postalCode</li><li>d_lat → latitude</li><li>d_longitude → longitude</li></ul> |
| `request_user_agent` | `ExperienceEvent.environment.browserDetails` <ul><li>h_user-agent → userAgent</li><li>h_accept-language → acceptLanguage</li></ul> |
| `client_ip` | `ExperienceEvent.environment` <ul><li>d_os_name → os name </li><li>d_os_version → os_version</li></ul> |
| `Signals` | ExperienceEvent.signals |

## Inbound data **(Deprecated)**

Type: ExperienceEvent

| Inbound Field |  XDM Field | 
| --- | --- |
| `uuid` | `ExperienceEvent.identityMap[<ID Type>]` |
| `deviceIds` | `ExperienceEvent.identityMap["CORE"] And calculated ECIDs  ExperienceEvent.identityMap["ECID"]` |
| `signals` | `ExperienceEvent.signals` |
| `b_time` | `ExperienceEvent.timeStamp` |
| `overwrite` | `overwriteTraits` |

>[!NOTE]
>
>Inbound Fields are scheduled to be deprecated in a future release.

## Profile data

Type: Profile XDM

| Profile Field | XDM Field |
| --- | --- |
| `ids` | `identityMap` |
| `smem` | `ExperienceEvent.segmentMemberships["AAMSegments"]` |
| `tmem` | `ExperienceEvent.segmentMemberships["AAMTraits"]` |
