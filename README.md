# Quartz v4

> “[One] who works with the door open gets all kinds of interruptions, but [they] also occasionally gets clues as to what the world is and what might be important.” — Richard Hamming

Quartz is a set of tools that helps you publish your [digital garden](https://jzhao.xyz/posts/networked-thought) and notes as a website for free.
Quartz v4 features a from-the-ground rewrite focusing on end-user extensibility and ease-of-use.

🔗 Read the documentation and get started: https://quartz.jzhao.xyz/

[Join the Discord Community](https://discord.gg/cRFFHYye7t)

## Sponsors

<p align="center">
  <a href="https://github.com/sponsors/jackyzha0">
    <img src="https://cdn.jsdelivr.net/gh/jackyzha0/jackyzha0/sponsorkit/sponsors.svg" />
  </a>
</p>




https://notes.nicolevanderhoeven.com/How+to+publish+Obsidian+notes+with+Quartz+on+GitHub+Pages#How+to+publish+Obsidian+notes+with+Quartz+on+GitHub+Pages


npx quartz sync
npx quartz build --serve




int maximum_path(vector<int> node_values) {
    //cout<<
    cout<<node_values.size()<< " size" <<endl;
    int depth = node_values.size();
    if(depth==1) return node_values[0]; //if there is only 1 node (base case

    queue<int> q; 
    q.push(0);
    int jump=1;
    int layer_size=1;
    int layer_count=0;
    
    vector<int> top_row;
    vector<int> bottom_row{0};
    bool top_to_bottom=false;
    int position=0;
    bool second_add = false;
    
    while(!q.empty()){
        int temp = q.front();
        cout<<temp<<'-'; //cout
        q.pop();
        if(top_to_bottom){
            bottom_row.push_back(top_row[position]+node_values[temp]);
            bottom_row.push_back(top_row[position]+node_values[temp]);
            position++;
            //cout<<" ="<<top_row[position]+node_values[temp]<<" position:" << position << "=";
        }else{
            top_row.push_back(bottom_row[position]+node_values[temp]);
            top_row.push_back(bottom_row[position]+node_values[temp]);
            position++;
            //cout<<" ="<<bottom_row[position]+node_values[temp]<<" position:" << position << "=";
        }

        if(temp+jump<depth){
                q.push(temp+jump);
                q.push(temp+jump+1);
        }
        layer_count++;
        if(layer_count==layer_size){
            top_to_bottom=!top_to_bottom;
            if(top_to_bottom){bottom_row.clear();}
            else{top_row.clear();};
            position=0;
            
            jump++;
            cout<<endl; //cout
            layer_count=0;
            if(layer_size==1){layer_size=2;}
            else{layer_size*=2;}
        }
    }
        if(top_row.size()>0){
            auto max_elem = max_element(top_row.begin(),top_row.end());
            return *max_elem;
        }else{
            auto max_elem = max_element(bottom_row.begin(),bottom_row.end());
            return *max_elem;
        }
        return 0;

}