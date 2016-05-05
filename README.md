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