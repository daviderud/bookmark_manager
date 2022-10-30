# bookmark_manager

An alternative bookmark manager for [SDR++](https://github.com/AlexandreRouma/SDRPlusPlus).

The original Frequency Manager included with the SDR++ has an inconvenience of arranging bookmarks in one row only, so they get overlapped:

![Overlapping bookmarks in SDR++ Frequency Manager](screenshots/sdrpp-overlapped-bookmarks.png?raw=true "Overlapping bookmarks in SDR++ Frequency Manager")

I really like SDR++ for its cleanliness, but this issue bugged me a lot. So I simply took the source of the Frequency Manager, copied it, renamed to Bookmark Manager and "fixed" it for myself.

Users can now choose to use between 1 and 7 lines for bookmarks to be automatically arranged:

![Bookmark Manager arranges bookmarks in sevral rows](screenshots/sdrpp-bookmark-manager.png?raw=true "Bookmark Manager arranges bookmarks in sevral rows")

Bookmarks with UTC, appropriate week days and currently not online are greyed out.

Additionally, by marking "Bookmark Rectangle" to off bookmarks are displayed in text-only, without fat rectangle around:

![Bookmark Manager arranges bookmarks in sevral rows](screenshots/sdrpp-bookmark-manager-text.png?raw=true "Bookmark Manager arranges bookmarks in sevral rows")


## Current Features

(As opposed to original Frequency Manager)

* Bookmark arrangement in up to 7 (user chosen) rows, both top and bottom arrangements
* Bookmarks can be displayed in text-only, without fat rectangle
* Cashed position for mouse-over (no recalculation)
* UTC start/end times of the broadcast (leave 0000 in both for all day broadcasts)
* Week days for a bookmark (all checked by default)

## Planned Features

I also have other plans for Bookmark Manager in the future:

* Give different colors for bookmark lists so they nice to identify
* Add a toggle to show/hide bookmarks that are not on time

## Compiling

Checkout the [SDR++](https://github.com/AlexandreRouma/SDRPlusPlus). Then checkout **bookmark_manager** into the **misc_modules** directory.

In SDR++'s **CMakeList.txt** file add the following lines

```
option(OPT_BUILD_BOOKMARK_MANAGER "Build the Bookmark Manager module" ON)
```

and

```
if (OPT_BUILD_BOOKMARK_MANAGER)
add_subdirectory("misc_modules/bookmark_manager")
endif (OPT_BUILD_BOOKMARK_MANAGER)
```

where appropriate.

Then compile all SDR++, `make install`, run it, add the Bookmarks Manager into your panel using Module Manager.

To migrate old bookmarks simply copy `frequency_manager.json` and rename it to `bookmark_manager.json`, then adjust the line number to a desired one.

