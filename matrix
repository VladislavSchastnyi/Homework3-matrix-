#include <iostream>
#include <cstring>

using namespace std;
int vyvodmatrix(int strok, int stolbchov, int **m){
    if (strok!=0){ 
        for(int i=0; i<strok; i++){
            for(int j=0; j<stolbchov; j++){
                cout << m[i][j] << ' ';
            }
            cout << endl;
        }
    }else{
        cout << "Матрица пустая " << endl;
    }
    return 0;
}

int umnogmatrix(int strok, int stolbchov, int **m){
    int **m1 = nullptr;
    int **m2 = nullptr;
    int i;
    int j;
    int k;
    char c;
    char s[255];
    int correct=1;
    int stolbchov1;
    int strok1;

    if (strok!=0){ 
        
        cout << "Введите размер матрицы: " << endl;
        
        cin >> s;
        
        
    	for(i=0; i<strlen(s); i++){
    	    c=(char)s[i];
    		
    		if((c<'0')||(c>'9')){
        		if((c=='x')&&(i!=0)){
        		    if( (strok1=atoi(s)) !=0){
            		    correct=0;
        		    }
        		}
    		    break;
    		}
        }
        
        if (correct==1){
            cerr << "Некорректный размер " << endl;
            return 1;
        }
        
        i++;
        
        if((stolbchov1=atoi(&(s[i]))) ==0){
            cerr << "Некорректный размер " << endl;
            return 1;
        }
        
    	for(; i<strlen(s); i++){
    	    c=(char)s[i];
    	    
    		if((c<'0')||(c>'9')){
        	    correct=1;
      		    break;
    		}
        }
        
        if (correct==1){
            cerr << "Некорректный размер " << endl;
            return 1;
        }
            
        if(strok != stolbchov1) {
            cerr << "Неверный размер " << endl;
            return 1;
        }
         
        
            
        m1 = new int * [strok1]; 
        for(i=0; i<strok1; i++){
            m1[i]=new int [stolbchov1];
        }
        
        m2 = new int * [strok]; 
        for(i=0; i<strok; i++){
            m2[i]=new int [stolbchov1];
        }
        
        for(i=0; i<strok1; i++) {
            for(j=0; j<stolbchov1; j++){
                cin >> m1[i][j];
            }
        }
        
        for(i=0; i<strok; i++) {
            for(j=0; j<stolbchov1; j++){
                m2[i][j]=0;
            }
        }
        
        for(i=0; i<strok; i++){
            for(j=0; j<stolbchov1; j++){
               for(k=0; k<stolbchov; k++) {
                    m2[i][j]+=m[i][k] * m1[k][j];
               }
            }   
        }
        
        vyvodmatrix(strok, stolbchov1, m2);
        
        for(i=0; i<strok; i++) {
            delete [] m2[i];
        }
        delete [] m2;
        for(i=0; i<strok1; i++) {
            delete [] m1[i];
        }
        delete [] m1;
        
    }else{
        cout << "Матрица пустая " << endl;
    }
    
    return 0;
}

int summatrix(int strok, int stolbchov, int **m){
    int **m1 = nullptr;
    int i;
    int j;

    if (strok!=0){ 

        m1 = new int * [strok]; 
        for(i=0; i<strok; i++){
            m1[i]=new int [stolbchov];
        }
        
        cout << "Введите матрицу " << strok << "x" << stolbchov << ":" << endl;
        
        for(i=0; i<strok; i++) {
            for(j=0; j<stolbchov; j++){
                cin >> m1[i][j];
            }
        }
        
        for(i=0; i<strok; i++){
            for(j=0; j<stolbchov; j++){
                m[i][j]=m[i][j] + m1[i][j];
            }
        }
        
        for(i=0; i<strok; i++) {
            delete [] m1[i];
        }
        delete [] m1;

    }else{
        cout << "Матрица пустая " << endl;
    }
    
    return 0;
}

int transportirovka (int strok, int stolbchov, int **m){
    int **m1 = nullptr;
    int i;
    int j;
    
    if (strok!=0){ 

        m1 = new int * [stolbchov]; 
        for(i=0; i<stolbchov; i++){
            m1[i]=new int [strok];
        }
        
        for(i=0; i<stolbchov; i++){
            for(j=0; j<strok; j++){
                m1[i][j]=m[j][i];
            }
        }
        
        vyvodmatrix(stolbchov, strok, m1);
        
        for(i=0; i<stolbchov; i++) {
            delete [] m1[i];
        }
        delete [] m1;

    }else{
        cout << "Матрица пустая " << endl;
    }
    
    return 0;
}

int vvodfile(int * strok, int * stolbchov, int * **m){   // передаём указатели на значения
  FILE *f;   // указатель на тип данных FILE
  char filename[255];
  char matrix[255];
  int i;
  char c;
  int correct=1;

  if ((*strok)==0){ 

    cout << "Укажите путь к файлу: ";
    cin >> filename ;

    if((f=fopen(filename, "r"))!=NULL){  // открываем файл в режиме для чтения
      fscanf(f, "%s", matrix);          // чтение строки из файла

      for(i=0; i<strlen(matrix); i++){
        c=(char)matrix[i];

        if((c<'0')||(c>'9')){
          if((c=='x')&&(i!=0)){
            if( ((*strok)=atoi(matrix)) !=0){
              correct=0;
            }
          }
          break;
        }
      }

      if (correct==0){
        i++;

        if(((*stolbchov)=atoi(&(matrix[i]))) ==0){
          correct=1;
        }else{

          for(; i<strlen(matrix); i++){
            c=matrix[i];

            if((c<'0')||(c>'9')){
              correct=1;
              break;
            }
          }
        }

        if (correct==0){
          (*m) = new int * [*strok]; 
          for(i=0; i<(*strok); i++){
            (*m)[i]=new int [*stolbchov];
          }

          for(i=0; i<(*strok); i++){
            for(int j=0; j<(*stolbchov); j++){
              (*m)[i][j]=0;
              if (fscanf(f, "%s", matrix) != EOF){  
                (*m)[i][j]=atoi(matrix);  
              }else{
                break;
              }
            }
          }
        }
      }
      
      if(correct==1){
        (*strok)=0;
        (*stolbchov)=0;
      }
      fclose(f);
    }else{
      cout << "Ошибка открытия файла" << endl;
    }
  }else{
    cout << "Матрица уже инициализирована " << endl;
  }

  return 0;
}

int vyvodfile(int strok, int stolbchov, int **m){
  FILE *f;
  char filename[255];
  char d='y';
  
  if (strok!=0){ 
    cout << "Укажите название файла:";
    cin >> filename ;

    if((f=fopen(filename, "r"))!=NULL){
      fclose(f);
      cout << "Перезаписать файл? (y, n): ";
      cin >> d;
    }

    if(d=='y'){
      if((f=fopen(filename, "w"))!=NULL){
        for(int i=0; i<strok; i++){
          for(int j=0; j<stolbchov; j++){
            fprintf(f, "%d ", m[i][j]);  // записываем эл-т в файл как число
          }
          fprintf(f, "\n");
        }
        fclose(f);
      }else{
        cout << "Error open file" << endl;
      }
    }
  }else{
    cout << "Матрица пустая " << endl;
  }

  return 0;
}

int classiksortirovka1(int strok, int stolbchov, int **m) {
    int i;
    int j;

    for (i = 0; i < strok * stolbchov; i++)
		for (j = 0; j < strok * stolbchov; j++) {
			if ((*m)[j] > (*m)[i]) swap((*m)[j], (*m)[i]);
		}

    return 1;		
}

int classiksortirovka(int strok, int stolbchov, int ***m) {
    int i;
    int j;
    int k;
	int *m1 = new int[strok * stolbchov];
	
	for (i = 0, k = 0; i < strok; i++)
		for (j = 0; j < stolbchov; j++) {
		    m1[k++] = (*m)[i][j];  // копирование эл-та матрицы в эл-т массива
		}
	classiksortirovka1(strok, stolbchov, &m1);
    
    for (i = 0, k = 0; i < strok; i++)
		for (j = 0; j < stolbchov; j++) (*m)[i][j] = m1[k++];

	delete[] m1;
}

int main(int argc,char*argv[]) {  // argv - массив указателей на строки параметров командной строки, argc - кол-во параметров + 1
	int **m=nullptr;   
    int i=0;
    int strok=0;
	int stolbchov=0;
	int correct=1;
	char c=0;
	char operation = 'c';
	
	if(argc!=1){  // проверка на наличие параметров входной строки
	
    	for(i=0; i<strlen(argv[1]); i++){  
    	    c=(char)argv[1][i];
    		
    		if((c<'0')||(c>'9')){
        		if((c=='x')&&(i!=0)){
        		    if( (strok=atoi(argv[1])) !=0){    // преобразование массива символов в число
            		    correct=0;
        		    }
        		}
    		    break;
    		}
        }
        
        if (correct==1){
            cerr << "Некорректная командная строка " << endl;
            return 1;
        }
        
        i++;
        
        if((stolbchov=atoi(&(argv[1][i]))) ==0){     
            cerr << "Некорректная командная строка " << endl;
            return 1;
        }
        
    	for(; i<strlen(argv[1]); i++){
    	    c=(char)argv[1][i];
    	    
    		if((c<'0')||(c>'9')){
        	    correct=1;
      		    break;
    		}
        }
    
        if (correct==1){
            cerr << "Некорректная командная строка " << endl;
            return 1;
        }
    
        m = new int * [strok];    // выделение памяти под указатели на столбцы
        for(i=0; i<strok; i++){
            m[i]=new int [stolbchov];
        }
    
        for(i=0; i<strok; i++){
            for(int j=0; j<stolbchov; j++){
                m[i][j]=0;
                if ((i*stolbchov+j+1+1)<argc){
                    m[i][j]=atoi(argv[i*stolbchov+j+1+1]);
                }
            }
        }
	}
    
    while(operation != 'e'){
        cout << endl;
        cout << "Выберите одну из операций:" << endl;
        cout << "1. Вывести матрицу" << endl;
        cout << "2. Сложить матрицу" << endl;
        cout << "3. Умножить матрицу" << endl;
        cout << "4. Транспонировать матрицу" << endl;
        cout << "5. Сохранить в файл" << endl;
        cout << "6. Загрузить из файла" << endl;
        cout << "7. Сортировать матрицу" << endl;

        cin >> operation;
    
        switch(operation){
            case '1':
                vyvodmatrix(strok, stolbchov, m);
            break;
            
            case '2':
                summatrix(strok, stolbchov, m);
            break;
            
            case '3':
                umnogmatrix(strok, stolbchov, m);
            break;
            
            case '4':
                transportirovka(strok, stolbchov, m);
            break;
            
            case '5':
                vyvodfile(strok, stolbchov, m);
            break;

            case '6':
              vvodfile(&strok, &stolbchov, &m);
            break;
            
            case '7':
              classiksortirovka(strok, stolbchov, &m);
            break;
     
            default:
                cerr << "Vveden nevernij parametr" << endl;
            break;
        }
    }

    for(i=0; i<strok; i++) {
        delete [] m[i];
    }
    delete [] m;

   return 0;	
}
