
# UNIVERSITY PROJECT (credit:LUMINAR) 

- Tik Tac Toe in c++

> [!warning]
> do not copy the program some update are left for specific purpose. use this as refference for your project to understand the working & basic concept of the program. 

- [x] work completed
- [ ] code clean
- [ ] some issue not resolve

## 📄 src code  

```
#include <iostream>
#include <vector>
using namespace std;
/*

arr={" 0 "," 1 "," 2 ",
     " 3 "," 4 "," 5 ",
	 " 6 "," 7 "," 8 ",};

*/

vector<string> arr={"   ","   ","   ",
					"   ","   ","   ",
					"   ","   ","   ",};
class user_id{


public:
	string usr_sym="  ";
	int user_no=0;
	void display(){
		int k=0;

		for(string j:arr){
			cout<< j <<" || ";
			k++;
			if (k==3 || k==6){
				cout<<endl;
				cout << "-------------------"<< endl;
			}
		}
		
	}

	int user_input(){
		int k;
		cout <<endl<< "user input"<< user_no <<" mark array [1-9]";
		cin>>k;
		try{
			if (k>=1 && k<=9){
				k=k-1;
				if (arr[k]==" x " || arr[k]==" 0 "){
					cout<<"value already exist"<<endl;
					return user_input();

				}else{
					return k; 
				}
			}else{
				throw k;
			}

		}catch(...){
			cout<< "mfc error invalid input"<<endl;
			return user_input();
		}
	}

	void change_array(int k){
		arr[k]=usr_sym;
	}
	
	bool check_h(){

		//horizontal logic
		for (int i=0 ;i<7;i+=3){
			//cout << arr[i] << arr[i+1] << arr[i+2] << endl;
			if (arr[i]==usr_sym && arr[i+1]==usr_sym && arr[i+2]==usr_sym){
				//cout << usr_sym <<' '<<'h'<<' '<< 1;
				return true;

			}
		}
		return false;
	}			

	bool check_v(){

		//Vertical logic
		for(int i=0 ;i<3; i++){
			//cout << arr[i] << arr[i+3] << arr[i+6] <<endl;
			if(arr[i]==usr_sym && arr[i+3]==usr_sym && arr[i+6]==usr_sym){
				//cout << usr_sym <<' '<<'v'<<' '<< 1;
				return true;	
			}
		} 

		return false;
	}	
		
	bool check_d(){
		//diagonal logic
		int i=0;
		//cout << arr[i] << arr[i+4] << arr[i+8];
		if(arr[i]==usr_sym && arr[i+4]==usr_sym && arr[i+8]==usr_sym ){
			//cout << usr_sym <<' '<<'d'<<' '<< 1;
			return true;
		}
		
		cout <<endl;
		i=2;
		//cout << arr[i] << arr[i+2] << arr[i+4];
		if (arr[i]==usr_sym && arr[i+2]==usr_sym && arr[i+4]==usr_sym){
			//cout << usr_sym <<' '<< "d2" <<' '<< 1;	
			return true;
		}

		return false;
		
	}

	bool win_validation(){
		if (check_h() || check_v() || check_d()){
			cout << endl;
			cout << "user " << user_no << " won"<< '[' << usr_sym << ']' <<endl;
			return true;
		}else{
			int count=0;
			for(string ch : arr){
				if (ch != "   "){
					count++;
				}
			}

			//cout << count;
			if (count==9){
				cout <<endl;
				cout << "tie";
				return true;
			}

		}
		
		return false;
	
	}

};


int user (){
	int inp;
	cout << "wann play with {x==>1;0==>2}";
	cin>> inp;
	return inp;

}



int main (){
	int x;
	bool loop=true;
	user_id user1;
	user_id user2;
	x=user();
	user1.user_no=1;
	user2.user_no=2;
	while (loop){
		//display();
		if (x==1){
			//order 1-2
			user1.usr_sym=" x ";
			user2.usr_sym=" 0 ";
			
		}else{
			//order 1-2
			user1.usr_sym=" 0 ";
			user2.usr_sym=" x ";

		}

		user1.change_array(user1.user_input());
		user1.display();
		if (user1.win_validation()){
			break;
		}

		user2.change_array(user2.user_input());
		user2.display();
		if (user2.win_validation()){
			break;
		}
	}

}



```