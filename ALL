// lec16
  // Snack
void sort_snacks(struct snack snacks[], int n) {
    struct snack *v[n];
    for(int i=0;i<n;i++){
        snacks[i].value = (double)snacks[i].weight / (double)snacks[i].price;
        v[i] = &snacks[i];
    }
    qsort(snacks, n, sizeof(struct snack), cmp);
}

int cmp(const void *a, const void *b) {
    struct snack aa = *(struct snack*)a;
    struct snack bb = *(struct snack*)b;
    if( aa.value < bb.value )
        return 1;
    else if ( aa.value > bb.value )
        return 0;
    else{
        if( aa.price > bb.price )
            return 1;
        else if ( aa.price < bb.price )
            return 0;
        else{
            if( aa.id > bb.id )
                return 1;
            else 
                return 0;
        }
    } 
}

  // online shop
void sum_total_costs(order_t orders[], unsigned order_cnt){
    for(int i=0;i<(int)order_cnt;i++){
        orders[i].total_cost = 0;
        for(unsigned j=0;j < orders[i].item_cnt; j++){
            item_t cur_item = orders[i].items[j];
            orders[i].total_cost += cur_item.cost * cur_item.cnt;
        }
    }
}

void reorder(order_t orders[], unsigned order_cnt){
    for(int i=0; i < (int)order_cnt ; i++){
        for(int j=0; j < (int)order_cnt - 1 ; j++){
            int j1_time = orders[j].pick_up_time.hour * 60 + orders[j].pick_up_time.minute ;
            int j2_time = orders[j+1].pick_up_time.hour * 60 + orders[j+1].pick_up_time.minute ;
            if ( j1_time > j2_time ){
                order_t tmp = orders[j] ;
                orders[j] = orders[j+1] ;
                orders[j+1] = tmp ;
            }
        }
    }
}

  // window

# define N 10000

Location *parse_url(char *url){
    int pos = strlen(url) - 1;
    if( url[pos] == '\n' )
        url[pos] = '\0';
    static Location loc = {.port = 0}, *p = &loc;
    char *tmp = strtok(url, "://");
    loc.protocol = tmp;

    tmp = strtok(NULL, "");
    while( *tmp == '/' ) tmp++; // sub :// last two elements
    
    // host and port
    int idx=0;
    char port[N], host[N], path[N], search[N], hash[N];
    host[0] = '\0' , path[0] = '\0', search[0] = '\0', hash[0] = '\0';
    loc.host = host, loc.pathname = path, loc.search = search, loc.hash = hash;

    while( 1 ){
        if( *(tmp + idx) == ':' || *(tmp + idx) == '/' || *(tmp + idx) == '\0' ){
            strncpy(host, tmp, idx);
            host[idx] = '\0';
            loc.host = host;
            tmp += idx + 1;
            if( *(tmp - 1) == ':' ){
                idx = 0;
                while(*(tmp + idx) != '/') idx++;
                strncpy(port, tmp, idx);
                port[idx] = '\0';
                loc.port = atoi(port);
                tmp += idx + 1;
            }
            break;
        }
        idx++;
    }

    // pathname
    idx = 0;
    while(1){
        if( *(tmp + idx) == '?' || *(tmp + idx) == '#' || *(tmp + idx) == '\0' ){
            strncpy(path, tmp, idx);
            path[idx] = '\0';
            loc.pathname = path;
            tmp += idx + 1;
            break;
        }
        idx++;
    }

    // search
    idx = 0;
    while(1){
        if( *(tmp + idx) == '#' || *(tmp + idx) == '\0' ){
            strncpy(search, tmp, idx);
            search[idx] = '\0';
            loc.search = search;
            tmp += idx + 1;
            break;
        }
        idx++;
    }

    idx = 0;
    while(1){
        if( *(tmp + idx) == '\0' ){
            strncpy(hash, tmp, idx);
            hash[idx] = '\0';
            loc.hash = hash;
            tmp += idx + 1;
            break;
        }
        idx++;
    }
    
    return p;
}




// lec16-2 Sly
#include<stdio.h>
#include<math.h>

int main(){
    int n, sum = 0, time = 7;
    scanf("%d", &n);
    for(int k=0;k<n;k++){
        float input;
        scanf("%f", &input);
        for(int i = 31; i >= 0; i--, time--){
            int tmp = (*(int *)&input >> i ) & 1 ;
            if (tmp) sum += pow(2, time);
            if (time == 0) time = 8;
        }
        if(sum%2) printf("Back\n");
        else printf("Front\n");
        sum = 0;
    }

    return 0;
}

// lec17 Magic

// lec20
  // XOR
#include<stdio.h>
#include<string.h>

void convert(char data, char key){
    int tmp = data^key;
    printf("%c", tmp);
}
int main(){
    int idx = 0;
    char key[2000], data[20000], ch;
    while(1){
        ch = getchar();
        if (ch == '\n' ) break;
        key[idx++] = ch;
    }
    idx = 0;
    while(1){
        ch = getchar();
        if (ch == '\n' ) break;
        data[idx++] = ch;
    }
    for(int i = 0 ; i < strlen(data) ; i++){
        convert(key[ i%(strlen(key)) ], data[i]);
    }
    return 0;
}

  // Bingo
  
