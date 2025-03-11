# Fableford Gazette Classifieds Ad Specification

## Overview
This document outlines the technical specifications for classifieds advertisements in the Fableford Gazette, which serves as both an in-world publication and a meta-level community coordination tool within the Testford/Fableford platform.

## File Format
All classified ads must be submitted as Markdown (.md) files with the following structure:

### Front Matter
Each classified ad file must begin with YAML front matter containing the following metadata:

```yaml
---
ad_id: GA000001
ad_type: collaboration_wanted
character_id: 2001
owner_id: 2001
parent_id: null
day: 1
title: "Descriptive Title of Advertisement"
status: active
---
```

### Front Matter Fields

| Field | Type | Description | Required | Format |
|-------|------|-------------|----------|--------|
| ad_id | String | Unique identifier for the ad | Yes | "GA" followed by 6-digit number (e.g., GA000001) |
| ad_type | String | Category of advertisement | Yes | One of: "collaboration_wanted", "character_request", "character_relationship", "collaboration_response", "event_announcement" |
| character_id | Integer | ID of the character placing the ad | Yes | Existing character ID from database |
| owner_id | Integer | ID of the character who owns the ad (matches character_id for original posts) | Yes | Existing character ID from database |
| parent_id | String or null | ID of the original ad if this is a response | No | Must be null for original ads; must be valid ad_id for responses |
| day | Integer | In-world day of publication | Yes | Matches the current Fableford timeline day |
| title | String | Short, descriptive title | Yes | Clear, concise description in title case |
| status | String | Current status of the ad | Yes | One of: "active", "pending", "fulfilled", "closed" |

## Ad Types and Content Structure

### 1. Collaboration Wanted
For characters seeking interaction with other established characters.

**Content Structure:**
- Headline (# Level 1 heading)
- Brief introduction of character and situation
- List of specific types of connections sought (bullet points)
- Brief description of potential narrative opportunities
- Optional writer's note (in italics)
- Contact information

### 2. Character Request
For requesting the creation of new characters needed for storylines.

**Content Structure:**
- Headline (# Level 1 heading)
- Brief explanation of the character role needed
- List of desired character attributes/qualities (bullet points)
- Brief description of how this character would fit into the narrative
- Contact information

### 3. Character Relationship
For requesting the creation of characters with specific relationships to existing characters.

**Content Structure:**
- Headline (# Level 1 heading)
- Brief description of the relationship being requested
- Character details section with specific attributes (bullet points)
- Narrative opportunities section outlining potential storylines
- Closing invitational statement
- Contact information

### 4. Collaboration Response
For responding to any of the above ad types.

**Content Structure:**
- Headline (# Level 1 heading with "RE: Original Ad Title")
- Opening greeting to original poster
- Explanation of proposed connection or response to request
- Details of potential interactions or character concept
- Questions or points for further discussion
- Closing statement of interest
- Contact information

### 5. Event Announcement
For announcing in-world events where multiple characters could interact.

**Content Structure:**
- Headline (# Level 1 heading)
- Date, time, and location details
- Brief description of the event
- List of potential participation opportunities (bullet points)
- Contact information for RSVP or questions

## Submission Guidelines

1. **Length**: Ads should be concise and typically range from 150-300 words.
2. **Formatting**: Use standard Markdown for formatting.
3. **Links**: Do not include external links.
4. **Images**: Images are not supported in classified ads.
5. **Character Reference**: Always include the character ID when referencing a character.

## Ad Lifecycle

1. **Creation**: Writer submits ad with status "active"
2. **Response**: Other writers may submit response ads with parent_id referencing the original
3. **Fulfillment**: When a request is satisfied, original poster updates status to "fulfilled"
4. **Closure**: Ads that are no longer relevant are updated to "closed" status

## Example
```markdown
---
ad_id: GA000001
ad_type: collaboration_wanted
character_id: 2001
owner_id: 2001
parent_id: null
day: 1
title: "Bookshop Owner Seeking Connections"
status: active
---

# BOOKSHOP OWNER SEEKING CONNECTIONS

Eleanor Frost (Character ID: 2001), the new owner of "Turning Pages" bookshop, is looking to establish connections within the Fableford community. As a recent returnee to town after fifteen years away, Eleanor is eager to:

- Meet fellow small business owners (especially café proprietors interested in possible book club collaborations)
- Connect with local writers or journalists who might be interested in hosting or covering literary events
- Encounter neighbors and regular customers who might become fixtures in her shop

Eleanor is particularly focused on revitalizing the town's literary scene and supporting local authors, though she tends to be reserved until she gets to know people. Her bookshop could serve as a natural meeting place for characters interested in literature, community events, or simply enjoying a quiet space.

*Writer's Note: Open to both casual interactions and more complex relationship development. Particularly interested in characters who might challenge Eleanor's tendency to keep people at arm's length.*

Contact: Eleanor-books (Discord)
```