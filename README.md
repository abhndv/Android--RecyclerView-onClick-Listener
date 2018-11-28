# Android-RecyclerView-onClick-Listener
A simple way to implement onClickListener in Android RecyclerView and obtain clicked position

First we create a interface RecyclerButtonClick with the function name which handles the click

    public interface RecyclerButtonClick {
        void onItemClick(int position);
    }

Then in the adapter file write function to pass click position to interface and set the onclicklistener to the item you click

    private RecyclerButtonClick click_position;
    ...
    public void onBindViewHolder(MyViewHolder holder, int position) {
        //init mAdapter
        ...
        mAdapter.setOnClick(FRAGMENT_NAME.this);
        ...
        holder.ITEM_NAME.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                click_position.onItemClick(position);
            }
        }); 
    }
    ...
    public void setOnClick(RecyclerButtonClick recyclerButtonClick)
    {
        this.click_position=recyclerButtonClick;
    }


Now bind the adapter in the fragment and write the function to implement what to do

    public class FRAGMENT_NAME extends Fragment implements RecyclerButtonClick{
  
    ...
    public void onItemClick(int position) {
        //WHAT TO DO ON CLICK
        Log.d("tag_name",rvclick+position);  //writes position to the log
    }
    
    ....
    }
    
In this YOUR_BUTTON should be the name of the thing in RecyclerView which you clicks
