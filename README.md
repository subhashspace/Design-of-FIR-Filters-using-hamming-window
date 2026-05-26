# 4-B-Design of FIR Filters using Hamming Window


### AIM:        
  To generate design of FIR digital filter using Hamming window in SCILAB .  

### APPARATUS REQUIRED: 
  PC Installed with SCILAB 

### PROGRAM 
#### a. Design of Low Pass FIR Digital filter
```python
clc;
close;
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = ');
alpha = (M-1)/2;
for n = 1:M
    if (n == alpha+1) then
        hd(n) = Wc/%pi;
    else
        hd(n) = sin(Wc*((n-1)-alpha))/(((n-1)-alpha)*%pi);
    end
end
// Hamming Window
for n = 1:M
    W(n) = 0.54 - 0.46*cos((2*%pi*(n-1))/(M-1));
end
h = hd .* W;
disp("Filter Coefficients:");
disp(h);
[hzm,fr] = frmag(h,256);
subplot(2,1,1)
plot(2*fr,hzm)
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Hamming Window');
hzm_dB = 20*log10(hzm);
subplot(2,1,2)
plot(2*fr,hzm_dB)
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude in dB');
title('Frequency Response of FIR LPF using Hamming Window');
```
#### b. Design of High Pass FIR Digital filter
```python
clc;
close;
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = ');
alpha = (M-1)/2;
for n = 1:M
    if (n == alpha+1) then
        hd(n) = 1 - (Wc/%pi);
    else
        hd(n) = -sin(Wc*((n-1)-alpha))/(((n-1)-alpha)*%pi);
    end
end
// Hamming Window
for n = 1:M
    W(n) = 0.54 - 0.46*cos((2*%pi*(n-1))/(M-1));
end
h = hd .* W;

disp("Filter Coefficients:");
disp(h);
[hzm,fr] = frmag(h,256);
subplot(2,1,1)
plot(2*fr,hzm)
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR HPF using Hamming Window');
hzm_dB = 20*log10(hzm);
subplot(2,1,2)
plot(2*fr,hzm_dB)
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude in dB');
title('Frequency Response of FIR HPF using Hamming Window');
```
#### c. Design of Band Pass FIR Digital filter
```python
clc ; 
close ; 
M=input('Enter the Odd Filter Length ='); 
Wc1 = input('Enter the Lower Cut off frequency = ');
Wc2 = input('Enter the Upper Cut off frequency = ');
alpha= (M -1)/2  
for n = 1:M 
    if (n ==alpha+1) 
        hd(n) =(Wc2-Wc1)/%pi ; 
    else 
        hd(n) =((sin(Wc2 *((n -1)-alpha)))-(sin(Wc1 *((n -1)-alpha))))/(((n -1)-alpha)*%pi);
    end 
end 
// Hamming Window 
for n = 1:M 
    W(n) = 0.54-(0.46*cos((2*%pi*(n-1))/(M-1))); 
end 
//Windowing filter coefficients 
h = hd.*W; 
disp('Filter Coefficients are') 
disp(h) 
[hzm,fr]= frmag (h,256) ; 
subplot(2 ,1 ,1) 
plot(2*fr, hzm) 
xlabel( ' Normalized Digital Frequency w'); 
ylabel( 'Magnitude '); 
title( ' Frequency Response of FIR BPF using Hamming Window ') 
hzm_dB = 20* log10 (hzm);
subplot (2 ,1 ,2); 
plot(2*fr , hzm_dB); 
xlabel( ' Normalized Digital Frequency W' ); 
ylabel( 'Magnitude in dB'); 
title('Frequency Response of FIR BPF using Hamming Window');
```
#### d. Design of Band Stop FIR Digital filter
```python
clc ; 
close ; 
M=input('Enter the Odd Filter Length ='); 
Wc1 = input('Enter the Lower Cut off frequency = ');
Wc2 = input('Enter the Upper Cut off frequency = ');
alpha= (M -1)/2 // Center Value 
for n = 1:M 
    if (n ==alpha+1) 
        hd(n) =1-((Wc2-Wc1)/%pi) ; 
    else 
        hd(n) =((sin(Wc1 *((n -1)-alpha)))-(sin(Wc2 *((n -1)-alpha))))/(((n -1)-alpha)*%pi); `  k,
    end 
end 
// Hamming Window 
for n = 1:M 
    W(n) = 0.54-(0.46*cos((2*%pi*(n-1))/(M-1)));  
end 
//Windowing filter coefficients 
h = hd.*W; 
disp('Filter Coefficients are') 
disp(h) 
[hzm,fr]= frmag (h,256) ; 
subplot(2 ,1 ,1) 
plot(2*fr, hzm) 
xlabel( ' Normalized Digital Frequency w'); 
ylabel( 'Magnitude '); 
title( ' Frequency Response of FIR BSF using Hamming Window ') 
hzm_dB = 20* log10 (hzm); 
subplot (2 ,1 ,2); 
plot(2*fr , hzm_dB); 
xlabel( ' Normalized Digital Frequency W' ); 
ylabel( 'Magnitude in dB'); 
title('Frequency Response of FIR BSF using Hamming Window');
```
### OUTPUT
#### a. Design of Low Pass FIR Digital filter
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/df79c54c-3caf-49b5-8cef-aff9d1e74e42" />
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/3acaceca-e831-4e56-bf19-a34ce0a75a15" />


#### b. Design of High Pass FIR Digital filter
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/6f349ba1-b57e-40b7-a83b-256b63da7f59" />
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/07a7989b-aa7e-4e6d-abe1-517652234fe5" />

#### c. Design of Band Pass FIR Digital filter
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/da31c0f9-6281-4909-814f-0441d9ed3e26" />
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/6ecef888-ab5e-4ea0-bc7d-019174aa46f9" />

#### d. Design of Band Stop FIR Digital filter
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/da7ee5e4-9d59-4b8f-bd1c-9fb37f10e788" />
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/4470ef7b-b656-4210-97b9-8bfdb0e1cf39" />

### RESULT
The FIR Filters were successfully designed using Hamming window Technique.
