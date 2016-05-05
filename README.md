# RecyclerViewUpdateRecoder
---
#### 1. Android Support Library, revision 21 (October 2014) 
**New v7 recyclerview library:**

- Added the RecyclerView widget, which provides a flexible list view for providing a limited window into a large data set.

#### 2. Android Support Library, revision 21.0.2 (November 2014)
**Changes for v7 recyclerview library:**

- Added TOUCH_SLOP_DEFAULT and TOUCH_SLOP_PAGING constants to the RecyclerView class to support touch slop configurations for paging.

#### 3. Android Support Library, revision 22 (March 2015)
**Changes for v7 recyclerview library:**

- Added the getlayoutPosition() and getadapterPosition() methods to the RecyclerView class.
- Deprecated the classgetChildPosition() and findViewHolderForPosition() methods in theRecyclerView class.
- Deprecated the getPosition() method in the RecyclerView.ViewHolder class.
- Deprecated the getViewPosition() method in the RecyclerView.LayoutParams class.

#### 4. Android Support Library, revision 22.1.0 (April 2015)
**Changes for v7 recyclerview library:**

- Added SortedList classes to display items in a list order and provide notification of changes to the list.
- Added the SortedListAdapterCallback class that can bind a sorted list to a RecyclerView.Adapterclass.

#### 5. Android Support Library, revision 23.1.0 (October 2015)

**Changes for v7 recyclerview library:**

- Added an improved animation API to the ItemAnimator class for better customizations:
  - Change animations no longer enforce two copies of the ViewHolder object, which enables item content animations. Also, the ItemAnimator object decides whether it wants to reuse the same ViewHolderobject or create a new one.
  - The new information record API gives the ItemAnimator class the flexibility to collect data at the correct point in the layout lifecycle. This information is later passed into the animate callbacks.
- Provided an easy transition plan for this backward-incompatible API change:
  - If you’ve previously extended the ItemAnimator class, you can change your base class to SimpleItemAnimator and your code should work as before. The SimpleItemAnimator class provides the old API by wrapping the new API.
  - Some methods were removed from the ItemAnimator class. The following code will no longer compile:
    
    ```java
  recyclerView.getItemAnimator().setSupportsChangeAnimations(false)
    ```
    You can replace it with:

    ```java
ItemAnimator animator = recyclerView.getItemAnimator();
	if (animator instanceof SimpleItemAnimator) {
	   ((SimpleItemAnimator) animator).setSupportsChangeAnimations(false);
	}
    ```

#### 6. Android Support Library, revision 23.1.1 (November 2015)

**Changes for v7 recyclerview library:**

- Fixed a crash that occurs when you perform a swipe-to-dismiss action that the ItemTouchHelper utility class provides, and then add an item. ([Issue 190500](http://b.android.com/190500 "Issue 190500"))

#### 7. Android Support Library, revision 23.2.0 (February 2016)

**Changes for v7 recyclerview library:**

- RecyclerView now has an opt-in feature called AutoMeasure which allows RecyclerView.LayoutManager to easily wrap content or handle various measurement specifications provided by the parent of theRecyclerView. It supports all existing animation capabilities of the RecyclerView.
- If you have a custom RecyclerView.LayoutManager, call setAutoMeasureEnabled(true) to start using the new AutoMeasure API. All built-in RecyclerView.LayoutManager objects enable auto-measure by default.
- RecyclerView.LayoutManager no longer ignores some RecyclerView.LayoutParams settings, such asMATCH_PARENT in the scroll direction.
Note: These lifted restrictions may cause unexpected behavior in your layouts. Make sure you specify the correct layout parameters.
- When updating a RecyclerView.ViewHolder with payload information, DefaultItemAnimator now disables change animations.
- You can now modify the ItemTouchHelper escape velocity to control swipe sensitivity. To make it easier or harder to swipe, override getSwipeEscapeVelocity(float defaultValue) and modify defaultValue.

#### 8. Android Support Library, revision 23.2.1 (March 2016)

**Changes for v7 recyclerview library:**

- Fixed bugs related to various measure-spec methods. (Issue 201856)
- Reduced the lockdown period in which RecyclerView does not allow adapter changes while calculating a layout or scroll. (Issue 202046)
- Fixed a crash when calling notifyItemChanged() on an item that is out of view. (Issue 202136)
- Fixed a crash that occurs when RecyclerView.LayoutManager adds and removes a view in the same measurement pass. (Issue 193958)

#### 9. Android Support Library, revision 23.3.0 (April 2016)

**Changes for v7 recyclerview library:**

- Fixed a bug where RecyclerView would not invoke scroll callbacks if the range of visible items shrank. (SimpleOnItemTouchListenerIssue 200987)
- Fixed a bug where RecyclerView would freeze if it was in linear layout, was weighted, and contained images. (Issue 203276)
- Fixed a crash in OrientationHelper.getStartAfterPadding(). (Issue 180521)
- Fixed a crash with usages of android:nestedScrollingEnabled. (Issue 197932)
