# Logging a shot

The **Shots** tab lists what you have logged, a day at a time. A shot holds
what the camera could not record about a frame taken with a manual lens: which
lens, at which aperture and focal length, what was on the lens, where you
were, and what you were after.

Tap **+** to log a new shot. The first time, the app asks you to add a lens
first (see [Your kit](kit.md)).

![The Shots tab: shots by day, each with its aperture, shutter speed, ISO, lens and note](../screenshots/app-shots-light.svg#only-light){ .phone loading=lazy }
![The Shots tab: shots by day, each with its aperture, shutter speed, ISO, lens and note](../screenshots/app-shots-dark.svg#only-dark){ .phone loading=lazy }
![The new shot form, with the lens, the focal length and the aperture](../screenshots/app-new-shot-light.svg#only-light){ .phone loading=lazy }
![The new shot form, with the lens, the focal length and the aperture](../screenshots/app-new-shot-dark.svg#only-dark){ .phone loading=lazy }

## What a shot holds

| Field | Notes |
|---|---|
| Date, time and time zone | They start as now. **Reset to now** puts them back. |
| Lens | Required. You choose it from your kit. |
| Focal length | Set by the lens when it has one focal length. For a lens with several fixed ones, such as a Tri-Elmar, choose one. |
| Aperture | An f-number, for example 3.2. When the lens has a widest and a narrowest aperture, the choices are the f-numbers from the widest to the narrowest, and a typed f-number outside them is refused. |
| Shutter speed | Optional, for example 1/1000, 0.5 or 3. Choose a usual value or type your own. |
| ISO | Optional. |
| Filters, lighting, accessories | Optional. You choose them from your kit. |
| Place | Text, as you would say it: "Where was this?". |
| Coordinates | Optional. See below. |
| Notes | Subject, light, intent, anything you want to keep. |

Tap **Save**, at the top, to keep it. It is the same when you edit a shot.

## Log the shot soon after you take it

The metadata writer finds which image each note is for by comparing times:
the time of the note with the time the camera recorded in the image. The
phone's time is the one the note gets, so:

- keep the phone's date and time set automatically;
- log the shot soon after taking it, within a few minutes if you can.

You do not need to know how far the camera's clock is out: the writer works
that out for you (see [How matching works](../writer/overview.md)).

## Where you were

**Place** is free text. **Coordinates** are separate: tap **Use current
location** and the app reads the phone's position, once, when you tap. The
first time, the phone asks you to allow it. Precise location has to be allowed:
an approximate one is too coarse to record.

By default the app also asks Apple (on iOS) or Google (on Android) for the name
of the place, which sends them the coordinates. A setting turns that off (see
[Settings and your data](settings.md)). **Clear coordinates** removes them from
a shot.

## Starting from the last shot

Often the next shot uses the same lens and aperture. In **Settings**, under
**Carry over**, you choose for each of these whether a new shot starts with the
value of the last shot: **Never**, **Same day** or **Always**.

- Lens, with its focal length and aperture
- Shutter speed
- ISO
- Kit: filters, lighting and accessories
- Note
- Place: the text only, never the coordinates

## Looking at, editing and deleting shots

Tap a shot to see all of it, to **Edit** it, or to open its place in a map app.

To act on several shots, tap **Select** at the top of the list, or press and
hold a shot. Tap the shots to choose them, or choose all the shots of a day. A
bar at the bottom then offers **Export** and **Delete**.

![One shot, with everything it holds](../screenshots/app-shot-light.svg#only-light){ .phone loading=lazy }
![One shot, with everything it holds](../screenshots/app-shot-dark.svg#only-dark){ .phone loading=lazy }
![The Shots tab with checkboxes, for choosing shots to export or delete](../screenshots/app-choosing-light.svg#only-light){ .phone loading=lazy }
![The Shots tab with checkboxes, for choosing shots to export or delete](../screenshots/app-choosing-dark.svg#only-dark){ .phone loading=lazy }

Deleting asks nothing. A bar with **Undo** is there for 10 seconds, and the
shots can be brought back for 30 days from **Settings**, **Recently deleted**.
After 30 days a deleted shot is erased for good.
