# Android-RecyclerView-onClick-Listener
A simple way to implement onClickListener in Android RecyclerView and obtain clicked position

First we create a class RecyclerButtonClick for passing value and implements the onclicklistener


    public class RecyclerButtonClick implements View.OnClickListener {
        YourFragment yourFragment;
        public int pos;

        public RecyclerButtonClick(int position){
            this.pos=position;
        }
        @Override
        public void onClick(View v) {
            yourFragment=new YourFragment();
            yourFragment.recyclerButtonClicked(pos);
        }
    }

Now that is set we can write what to do in your Fragment java file function.
It is then called by creating and instance of the Fragment.

    public void recyclerButtonClicked(int position) {
        ...
        //position will have the index value of the rows in RecyclerView.
        ...
    }

Now we need to call the RecyclerButtonClick class in setOnClickListener
We give that in the onBindViewHolder()

    public void onBindViewHolder(MyViewHolder holder, int position) {
        ...
        holder.YOUR_BUTTON.setOnClickListener(new RecyclerButtonClick(position));
        ...
    }
    
In this YOUR_BUTTON should be the name of the thing in RecyclerView which you clicks
