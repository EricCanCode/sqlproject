# sqlproject
a sample database for a movie store

SQL> CREATE TABLE DISTRIBUTORS
  2  (
  3      Dist_ID    int NOT NULL,
  4      Dist_Code  varchar(20) NOT NULL,
  5      Movie_Name varchar(60) NOT NULL,
  6      Actor_Actress  varchar(500) NOT NULL,
  7      Running_Length int          NOT NULL,
  8      Genre          varchar(30)  NOT NULL,
  9      Rating         varchar(6)   NOT NULL,
 10      Year_Released  int          NOT NULL,
 11      Director       varchar(255) NOT NULL,
 12      Academy_Awards varchar(255) NOT NULL,
 13      Price      dec(3, 2)   NOT NULL,
 14      PRIMARY KEY (Dist_ID)
 15  );

Table created.

SQL> INSERT INTO DISTRIBUTORS (Dist_ID, Dist_Code, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Price)
  3  VALUES (1, 'DVD_QS1', 'QUEEN_AND_SLIM', 'Daniel Kaluuya, Jodie Turner-Smith, Bokeem Woodbine, Chloë Sevigny, Flea,
  4          Sturgill Simpson, Indya Moore, Benito Martinez, Jahi DiAllo Winston,NGralen Bryant Banks,
  5          Dickson Obahor, Bryant Tardy, Thom Gossom Jr., Melanie Halfkenny',
  6          132,
  7          'ROMANCE/DRAMA',
  8          'R',
  9          2019,
 10          'Melina Matsoukas',
 11          'NONE',
 12          4.99);

1 row created.

SQL> INSERT INTO DISTRIBUTORS (Dist_ID, Dist_Code, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Price)
  3  VALUES (2,
  4          'DVD_GO1',
  5          'GET_OUT',
  6          'Daniel Kaluuya, Allison Williams, Bradley Whitford, Caleb Landry Jones,
  7          Stephen Root, Catherine Keener',
  8          132,
  9          'THRILLER',
 10          'R',
 11          2017,
 12          'Jordan Peele',
 13          'Best Picture, Best Director, Best Original Screenplay, and Best Actor - Academy Awards 2017',
 14          4.99);

1 row created.

SQL> INSERT INTO DISTRIBUTORS (Dist_ID, Dist_Code, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Price)
  3  VALUES (3,
  4          'DVD_HAM1',
  5          'HAMILTON',
  6          'Lin-Manuel Miranda,Phillipa Soo, Leslie Odom Jr., Renée Elise Goldsberry,
  7          Daveed Diggs, Christopher Jackson, Okieriete Onaodowan, Jasmine Cephas Jones,
  8          Anthony Ramos,Jonathan Groff',
  9          160,
 10          'MUSICAL',
 11          'PG-13',
 12          2020,
 13          'Thomas Kail',
 14          'NONE',
 15          4.99);

1 row created.

SQL> INSERT INTO DISTRIBUTORS (Dist_ID, Dist_Code, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Price)
  3  VALUES (4,
  4          'DVD_SPDRMAN5',
  5          'SPIDERMAN_INTO_THE_SPIDER-VERSE',
  6          'Shameik Moore, Jake Johnson, Hailee Steinfeld, Mahershala Ali,
  7          Brian Tyree Henry, Lily Tomlin, Luna Lauren Velez, John Mulaney, Kimiko Glenn,
  8          Nicolas Cage, Liev Schreiber',
  9          117,
 10          'ACTION/ADVENTURE',
 11          'PG',
 12          2018,
 13          'Bob Persichetti, Peter Ramsey, Rodney Rothman',
 14          'Best Animated Feature - Academy_Awards_2018',
 15          4.99);

1 row created.

SQL> INSERT INTO DISTRIBUTORS (Dist_ID, Dist_Code, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Price)
  3  VALUES (5,
  4          'DVD_HFIGURES1',
  5          'HIDDEN_FIGURES',
  6          'Taraji P. Henson, Octavia Spencer, Janelle Monáe, Kevin Costner, Kirsten Dunst, Jim Parsons',
  7          127,
  8          'BIOGRAPHY/DRAMA',
  9          'PG',
 10          2016,
 11          'Theodore Melfi',
 12          'Best Adapted Screenplay, Best Picture, and Best Supporting Actress - Academy_Awards_2016',
 13          4.99);

1 row created.

SQL> CREATE TABLE MPINVENTORY
  2  (
  3      MPInv_ID   int         NOT NULL,
  4      Movie_Name varchar(60) NOT NULL,
  5      Dist_ID    int NOT NULL,
  6      Price      dec(3, 2)   NOT NULL,
  7      Discounts  int         NOT NULL,
  8      PRIMARY KEY (MPInv_ID),
  9      FOREIGN KEY (Dist_ID) REFERENCES DISTRIBUTORS (Dist_ID)
 10  );

Table created.

SQL> INSERT INTO MPINVENTORY (MPInv_ID, Movie_Name, Dist_ID, Price, Discounts)
  2  VALUES (41719101,
  3          'QUEEN_AND_SLIM',
  4          1,
  5          4.99,
  6          0.49);

1 row created.

SQL> 
SQL> INSERT INTO MPINVENTORY (MPInv_ID, Movie_Name, Dist_ID, Price, Discounts)
  2  VALUES (47520101,
  3          'GET_OUT',
  4          2,
  5          4.99,
  6          0.49);

1 row created.

SQL> 
SQL> INSERT INTO MPINVENTORY (MPInv_ID, Movie_Name, Dist_ID, Price, Discounts)
  2  VALUES (48113101,
  3          'HAMILTON',
  4          3,
  5          4.99,
  6          0.49);

1 row created.

SQL> 
SQL> INSERT INTO MPINVENTORY (MPInv_ID, Movie_Name, Dist_ID, Price, Discounts)
  2  VALUES (41916101,
  3          'SPIDERMAN_INTO_THE_SPIDER-VERSE',
  4          4,
  5          4.99,
  6          0.49);

1 row created.

SQL> 
SQL> INSERT INTO MPINVENTORY (MPInv_ID, Movie_Name, Dist_ID, Price, Discounts)
  2  VALUES (48944101,
  3          'HIDDEN_FIGURES',
  4          5,
  5          4.99,
  6          0.49);

1 row created.

SQL> CREATE TABLE CUSTOMERS
  2  (
  3      Cust_Name    varchar(30)    NOT NULL,
  4      Cust_Street  varchar(60)    NOT NULL,
  5      Cust_ZipCode numeric(5, 0)  NOT NULL,
  6      Cust_Phone   numeric(10, 0) NOT NULL,
  7      Movie_Name   varchar(60)    NOT NULL,
  8      Rental_Date  date    NOT NULL,
  9      Return_Date  date    NOT NULL,
 10      Fees         dec(3, 2),
 11      Damages      dec(3, 2),
 12      Discounts    dec(3, 2),
 13      PRIMARY KEY (Cust_Name)
 14  );

Table created.

SQL> INSERT INTO CUSTOMERS (Cust_Name, Cust_Street, Cust_ZipCode, Cust_Phone, Movie_Name, Rental_Date,
  2                             Return_Date, Fees, Damages, Discounts)
  3  VALUES ('Susie Newbie',
  4          '123 Peakaboo Lane',
  5          12345,
  6          1112223333,
  7          'QUEEN_AND_SLIM',
  8          '20-jul-25',
  9          '20-jul-28',
 10          0.00,
 11          0.00,
 12          0.00);

1 row created.

SQL> INSERT INTO CUSTOMERS (Cust_Name, Cust_Street, Cust_ZipCode, Cust_Phone, Movie_Name, Rental_Date, Return_Date, Fees,
  2                             Damages, Discounts)
  3  VALUES ('Ralpheez MadeUp',
  4          '1 TwoThree Lane',
  5          54321,
  6          1234567890,
  7          'HAMILTON',
  8          '20/jul/24',
  9          '20/jul/27',
 10          3.25,
 11          0,
 12          1.00);

1 row created.

SQL> INSERT INTO CUSTOMERS (Cust_Name, Cust_Street, Cust_ZipCode, Cust_Phone, Movie_Name, Rental_Date, Return_Date, Fees,
  2                             Damages, Discounts)
  3  VALUES ('John DaMan',
  4          '456 CheckMy Drive',
  5          23456,
  6          4445556666,
  7          'GET_OUT',
  8          '20/may/12',
  9          '20/may/20',
 10          3.25,
 11          9.99,
 12          0);

1 row created.

SQL> INSERT INTO CUSTOMERS (Cust_Name, Cust_Street, Cust_ZipCode, Cust_Phone, Movie_Name, Rental_Date, Return_Date, Fees,
  2                             Damages, Discounts)
  3  VALUES ('Teresa Ishername',
  4          '1 Stepaway Corner',
  5          22222,
  6          3456789012,
  7          'SPIDERMAN_INTO_THE_SPIDER-VERSE',
  8          '20/jul/10',
  9          '20/jul/13',
 10          0,
 11          0,
 12          1.00);

1 row created.

SQL> INSERT INTO CUSTOMERS (Cust_Name, Cust_Street, Cust_ZipCode, Cust_Phone, Movie_Name, Rental_Date, Return_Date, Fees,
  2                             Damages, Discounts)
  3  VALUES ('Taraji Washere',
  4          '4 Myempire Place',
  5          23232,
  6          9876543210,
  7          'HIDDEN_FIGURES',
  8          '20/jul/18',
  9          '20/jul/21',
 10          0,
 11          0,
 12          1.00);

1 row created.

SQL> CREATE TABLE RENTALS
  2  (
  3      Cust_Name   varchar(30) NOT NULL,
  4      Movie_Name  varchar(60) NOT NULL,
  5      Rental_Date DATE        NOT NULL,
  6      Return_Date DATE        NOT NULL,
  7      Dist_ID     int         NOT NULL,
  8      MPInv_ID    int         NOT NULL,
  9      Price       dec(3, 2)   NOT NULL,
 10      Taxes       dec(3, 2)   NOT NULL,
 11      Fees        dec(3, 2),
 12      Discounts   dec(3, 2),
 13      PRIMARY KEY (Rental_Date),
 14      FOREIGN KEY (Dist_ID) REFERENCES DISTRIBUTORS (Dist_ID),
 15      FOREIGN KEY (MPInv_ID) REFERENCES MPINVENTORY (MPInv_ID),
 16      FOREIGN KEY (Cust_Name) REFERENCES CUSTOMERS (Cust_Name)
 17  );

Table created.

SQL> INSERT INTO RENTALS (Cust_Name, Movie_Name, Rental_Date, Return_Date, Dist_ID, MPInv_ID, Price,
  2                           Taxes, Fees, Discounts)
  3  VALUES ('Susie Newbie',
  4          'QUEEN_AND_SLIM',
  5          '20/jul/25',
  6          '20/jul/28',
  7          1,
  8          41719101,
  9          4.99,
 10          0.49,
 11          0,
 12          0);

1 row created.

SQL> INSERT INTO RENTALS (Cust_Name, Movie_Name, Rental_Date, Return_Date, Dist_ID, MPInv_ID, Price,
  2                           Taxes, Fees, Discounts)
  3  VALUES ('John DaMan',
  4          'GET_OUT',
  5          '20/may/12',
  6          '20/may/20',
  7          2,
  8          47520101,
  9          4.99,
 10          0.49,
 11          3.25,
 12          0);

1 row created.

SQL> INSERT INTO RENTALS (Cust_Name, Movie_Name, Rental_Date, Return_Date, Dist_ID, MPInv_ID, Price,
  2                           Taxes, Fees, Discounts)
  3  VALUES ('Ralpheez MadeUp',
  4          'HAMILTON',
  5          '20/jul/24',
  6          '20/jul/27',
  7          3,
  8          48113101,
  9          4.99,
 10          0.49,
 11          3.25,
 12          1.00);

1 row created.

SQL> INSERT INTO RENTALS (Cust_Name, Movie_Name, Rental_Date, Return_Date, Dist_ID, MPInv_ID, Price,
  2                           Taxes, Fees, Discounts)
  3  VALUES ('Teresa Ishername',
  4          'SPIDERMAN_INTO_THE_SPIDER-VERSE',
  5          '20/jul/10',
  6          '20/jul/13',
  7          4,
  8          41916101,
  9          4.99,
 10          0.49,
 11          0,
 12          1.00);

1 row created.

SQL> INSERT INTO RENTALS (Cust_Name, Movie_Name, Rental_Date, Return_Date, Dist_ID, MPInv_ID, Price,
  2                           Taxes, Fees, Discounts)
  3  VALUES ('Taraji Washere',
  4          'HIDDEN_FIGURES',
  5          '20/jul/18',
  6          '20/jul/21',
  7          5,
  8          48944101,
  9          4.99,
 10          0.49,
 11          0,
 12          1.00);

1 row created.

SQL> CREATE TABLE STOREHUB
  2  (
  3      MP_IDNum     INT            NOT NULL,
  4      Dist_ID      int            NOT NULL,
  5      Dist_Code    varchar(20)    NOT NULL,
  6      MPInv_ID     INT            NOT NULL,
  7      Movie_Name   varchar(60)    NOT NULL,
  8      Actor_Actress  varchar(500) NOT NULL,
  9      Running_Length int          NOT NULL,
 10      Genre          varchar(30)  NOT NULL,
 11      Rating         varchar(6)   NOT NULL,
 12      Year_Released  int          NOT NULL,
 13      Director       varchar(255) NOT NULL,
 14      Academy_Awards varchar(255) NOT NULL,
 15      Rental_Date  DATE           NOT NULL,
 16      Return_Date  DATE           NOT NULL,
 17      Cust_Name    varchar(30)    NOT NULL,
 18      Cust_Street  varchar(60)    NOT NULL,
 19      Cust_ZipCode Numeric(5, 0)  NOT NULL,
 20      Cust_Phone   NUMERIC(10, 0) NOT NULL,
 21      Taxes        dec(3, 2)      NOT NULL,
 22      Fees         dec(3, 2)      NOT NULL,
 23      Damages      dec(3, 2)      NOT NULL,
 24      Discounts    dec(3, 2)       NOT NULL,
 25      PRIMARY KEY (MP_IDNum),
 26      FOREIGN KEY (Dist_ID) REFERENCES DISTRIBUTORS (Dist_ID),
 27      FOREIGN KEY (MPInv_ID) REFERENCES MPINVENTORY (MPInv_ID),
 28      FOREIGN KEY (Rental_Date) REFERENCES RENTALS (Rental_Date),
 29      FOREIGN KEY (Cust_Name) REFERENCES CUSTOMERS (Cust_Name)
 30  );

Table created.

SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (41719,
  5          1,
  6          'DVD_QS1',
  7          41719101,
  8          'QUEEN_AND_SLIM',
  9          'Daniel Kaluuya, Jodie Turner-Smith, Bokeem Woodbine, Chloë Sevigny, Flea,
 10          Sturgill Simpson, Indya Moore, Benito Martinez, Jahi DiAllo Winston,NGralen Bryant Banks,
 11          Dickson Obahor, Bryant Tardy, Thom Gossom Jr., Melanie Halfkenny',
 12          132,
 13          'ROMANCE/DRAMA',
 14          'R',
 15          2019,
 16          'Melina Matsoukas',
 17          'NONE',
 18          '20/jul/25',
 19          '20/jul/28',
 20          'Susie Newbie',
 21          '123 Peakaboo Lane',
 22          12345,
 23          1112223333,
 24          0.49,
 25          0.00,
 26          0.00,
 27          0.00);

1 row created.

SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards,Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (47520,
  5          2,
  6          'DVD_GO1',
  7          47520101,
  8          'GET_OUT',
  9          'Daniel Kaluuya, Allison Williams, Bradley Whitford, Caleb Landry Jones,
 10          Stephen Root, Catherine Keener',
 11          132,
 12          'THRILLER',
 13          'R',
 14          2017,
 15          'Jordan Peele',
 16          'Best Picture, Best Director, Best Original Screenplay, and Best Actor - Academy Awards 2017',
 17          '20/may/12',
 18          '20/may/20',
 19          'John DaMan',
 20          '456 CheckMy Drive',
 21          23456,
 22          4445556666,
 23          0.49,
 24          3.25,
 25          9.99,
 26          0);

1 row created.

SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                          Academy_Awards,Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (48113,
  5          3,
  6          'DVD_HAM1',
  7          48113101,
  8          'HAMILTON',
  9          'Lin-Manuel Miranda,Phillipa Soo, Leslie Odom Jr., Renée Elise Goldsberry,
 10          Daveed Diggs, Christopher Jackson, Okieriete Onaodowan, Jasmine Cephas Jones,
 11          Anthony Ramos,Jonathan Groff',
 12          160,
 13          'MUSICAL',
 14          'PG-13',
 15          2020,
 16          'Thomas Kail',
 17          'NONE',
 18          '20/jul/24',
 19          '20/jul/27',
 20          'Ralpheez MadeUp',
 21          '1 TwoThree Lane',
 22          54321,
 23          1234567890,
 24          0.49,
 25          3.49,
 26          0,
 27          1.00);

1 row created.

SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (41916,
  5          4,
  6          'DVD_SPDRMAN5',
  7          41916101,
  8          'SPIDERMAN_INTO_THE_SPIDER-VERSE',
  9          'Shameik Moore, Jake Johnson, Hailee Steinfeld, Mahershala Ali,
 10          Brian Tyree Henry, Lily Tomlin, Luna Lauren Velez, John Mulaney, Kimiko Glenn,
 11          Nicolas Cage, Liev Schreiber',
 12          117,
 13          'ACTION/ADVENTURE',
 14          'PG',
 15          2018,
 16          'Bob Persichetti, Peter Ramsey, Rodney Rothman',
 17          'Best Animated Feature - Academy_Awards_2018',
 18          '20/jul/10',
 19          '20/jul/13',
 20          'Teresa Ishername',
 21          '1 Stepaway Corner',
 22          22222,
 23          3456789012,
 24          0.49,
 25          0,
 26          0,
 27          1.00);

1 row created.

SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards,Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (48944,
  5          5,
  6          'DVD_HFigures1',
  7          48944101,
  8          'HIDDEN_FIGURES',
  9          'Taraji P. Henson, Octavia Spencer, Janelle Monáe, Kevin Costner, Kirsten Dunst, Jim Parsons',
 10          127,
 11          'BIOGRAPHY/DRAMA',
 12          'PG',
 13          2016,
 14          'Theodore Melfi',
 15          'Best Adapted Screenplay, Best Picture, and Best Supporting Actress - Academy_Awards_2016',
 16          '20/jul/18',
 17          '20/jul/21',
 18          'Taraji Istaken',
 19          '4 Myempire Place',
 20          23232,
 21          9876543210,
 22          0.49,
 23          0,
 24          0,
 25          1.00);
INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
*
ERROR at line 1:
ORA-02291: integrity constraint (CM320R09.SYS_C003268879) violated - parent key 
not found 


SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards,Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (48944,
  5          5,
  6          'DVD_HFigures1',
  7          48944101,
  8          'HIDDEN_FIGURES',
  9          'Taraji P. Henson, Octavia Spencer, Janelle Monáe, Kevin Costner, Kirsten Dunst, Jim Parsons',
 10          127,
 11          'BIOGRAPHY/DRAMA',
 12          'PG',
 13          2016,
 14          'Theodore Melfi',
 15          'Best Adapted Screenplay, Best Picture, and Best Supporting Actress - Academy_Awards_2016',
 16          '20/jul/18',
 17          '20/jul/21',
 18          'Taraji Washere',
 19          '4 Myempire Place',
 20          23232,
 21          9876543210,
 22          0.49,
 23          0,
 24          0,
 25          1.00);

1 row created.

SQL> SELECT Cust_Name, Cust_Street, Cust_ZipCode FROM CUSTOMERS;

CUST_NAME                                                                       
------------------------------                                                  
CUST_STREET                                                  CUST_ZIPCODE       
------------------------------------------------------------ ------------       
Susie Newbie                                                                    
123 Peakaboo Lane                                                   12345       
                                                                                
Ralpheez MadeUp                                                                 
1 TwoThree Lane                                                     54321       
                                                                                
John DaMan                                                                      
456 CheckMy Drive                                                   23456       
                                                                                

CUST_NAME                                                                       
------------------------------                                                  
CUST_STREET                                                  CUST_ZIPCODE       
------------------------------------------------------------ ------------       
Teresa Ishername                                                                
1 Stepaway Corner                                                   22222       
                                                                                
Taraji Washere                                                                  
4 Myempire Place                                                    23232       
                                                                                

SQL> SELECT Cust_Name, Movie_Name, Rental_Date, Return_Date FROM RENTALS WHERE Rental_Date BETWEEN '20-JUL-01' AND '20-JUL-30' ORDER BY Rental_Date;

CUST_NAME                                                                       
------------------------------                                                  
MOVIE_NAME                                                   RENTAL_DA RETURN_DA
------------------------------------------------------------ --------- ---------
Teresa Ishername                                                                
SPIDERMAN_INTO_THE_SPIDER-VERSE                              20-JUL-10 20-JUL-13
                                                                                
John DaMan                                                                      
GET_OUT                                                      20-MAY-12 20-MAY-20
                                                                                
Taraji Washere                                                                  
HIDDEN_FIGURES                                               20-JUL-18 20-JUL-21
                                                                                

CUST_NAME                                                                       
------------------------------                                                  
MOVIE_NAME                                                   RENTAL_DA RETURN_DA
------------------------------------------------------------ --------- ---------
Ralpheez MadeUp                                                                 
HAMILTON                                                     20-JUL-24 20-JUL-27
                                                                                
Susie Newbie                                                                    
QUEEN_AND_SLIM                                               20-JUL-25 20-JUL-28
                                                                                

SQL> SELECT Dist_ID, Dist_Code, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Price From DISTRIBUTORS ORDER BY Dist_ID;

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
         1 DVD_QS1                                                              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
QUEEN_AND_SLIM                                                                  

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Daniel Kaluuya, Jodie Turner-Smith, Bokeem Woodbine, Chlo? Sevigny, Flea,       

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Sturgill Simpson, Indya Moore, Benito Martinez, Jahi DiAllo Winston,NGra

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
len Bryant Banks,                                                               

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Dickson Obahor, Bryant Tardy, Thom Gossom Jr., Melanie Halfkenny        

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
           132 ROMANCE/DRAMA                  R               2019              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Melina Matsoukas                                                                

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
NONE                                                                            

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
      4.99                                                                      

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
                                                                                

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
         2 DVD_GO1                                                              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
GET_OUT                                                                         

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Daniel Kaluuya, Allison Williams, Bradley Whitford, Caleb Landry Jones,         

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Stephen Root, Catherine Keener                                          

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
           132 THRILLER                       R               2017              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Jordan Peele                                                                    

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Best Picture, Best Director, Best Original Screenplay, and Best Actor - Academy 

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Awards 2017                                                                     

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
      4.99                                                                      

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
                                                                                

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
         3 DVD_HAM1                                                             

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
HAMILTON                                                                        

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Lin-Manuel Miranda,Phillipa Soo, Leslie Odom Jr., Ren?e Elise Goldsberry,       

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Daveed Diggs, Christopher Jackson, Okieriete Onaodowan, Jasmine Cephas J

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
ones,                                                                           

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Anthony Ramos,Jonathan Groff                                            

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
           160 MUSICAL                        PG-13           2020              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Thomas Kail                                                                     

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
NONE                                                                            

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
      4.99                                                                      

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
                                                                                

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
         4 DVD_SPDRMAN5                                                         

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
SPIDERMAN_INTO_THE_SPIDER-VERSE                                                 

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Shameik Moore, Jake Johnson, Hailee Steinfeld, Mahershala Ali,                  

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Brian Tyree Henry, Lily Tomlin, Luna Lauren Velez, John Mulaney, Kimiko 

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Glenn,                                                                          

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
        Nicolas Cage, Liev Schreiber                                            

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
           117 ACTION/ADVENTURE               PG              2018              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Bob Persichetti, Peter Ramsey, Rodney Rothman                                   

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Best Animated Feature - Academy_Awards_2018                                     

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
      4.99                                                                      

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
                                                                                

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
         5 DVD_HFIGURES1                                                        

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
HIDDEN_FIGURES                                                                  

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Taraji P. Henson, Octavia Spencer, Janelle Mon?e, Kevin Costner, Kirsten Dunst, 

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Jim Parsons                                                                     

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
           127 BIOGRAPHY/DRAMA                PG              2016              

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Theodore Melfi                                                                  

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
Best Adapted Screenplay, Best Picture, and Best Supporting Actress - Academy_Awa

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
rds_2016                                                                        

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
      4.99                                                                      

   DIST_ID DIST_CODE                                                            
---------- --------------------                                                 
MOVIE_NAME                                                                      
------------------------------------------------------------                    
ACTOR_ACTRESS                                                                   
--------------------------------------------------------------------------------
RUNNING_LENGTH GENRE                          RATING YEAR_RELEASED              
-------------- ------------------------------ ------ -------------              
DIRECTOR                                                                        
--------------------------------------------------------------------------------
ACADEMY_AWARDS                                                                  
--------------------------------------------------------------------------------
     PRICE                                                                      
----------                                                                      
                                                                                

SQL> delete from storehub where cust_name = 'Taraji Washere';

1 row deleted.

SQL> delete from rentals where cust_name = 'Taraji Washere';

1 row deleted.

SQL> update customers set cust_name = 'Taraji Istaken' where cust_name = 'Taraji Washere';

1 row updated.

SQL> INSERT INTO RENTALS (Cust_Name, Movie_Name, Rental_Date, Return_Date, Dist_ID, MPInv_ID, Price,
  2                           Taxes, Fees, Discounts)
  3  VALUES ('Taraji Istaken',
  4          'HIDDEN_FIGURES',
  5          '20/jul/18',
  6          '20/jul/21',
  7          5,
  8          48944101,
  9          4.99,
 10          0.49,
 11          0,
 12          1.00);

1 row created.

SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards, Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (41916,
  5          4,
  6          'DVD_SPDRMAN5',
  7          41916101,
  8          'SPIDERMAN_INTO_THE_SPIDER-VERSE',
  9          'Shameik Moore, Jake Johnson, Hailee Steinfeld, Mahershala Ali,
 10          Brian Tyree Henry, Lily Tomlin, Luna Lauren Velez, John Mulaney, Kimiko Glenn,
 11          Nicolas Cage, Liev Schreiber',
 12          117,
 13          'ACTION/ADVENTURE',
 14          'PG',
 15          2018,
 16          'Bob Persichetti, Peter Ramsey, Rodney Rothman',
 17          'Best Animated Feature - Academy_Awards_2018',
 18          '20/jul/10',
 19          '20/jul/13',
 20          'Teresa Ishername',
 21          '1 Stepaway Corner',
 22          22222,
 23          3456789012,
 24          0.49,
 25          0,
 26          0,
 27          1.00);
INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
*
ERROR at line 1:
ORA-00001: unique constraint (CM320R09.SYS_C003268875) violated 


SQL> INSERT INTO STOREHUB (MP_IDNum, Dist_ID, Dist_Code, MPInv_ID, Movie_Name, Actor_Actress, Running_Length, Genre, Rating, Year_Released, Director,
  2                            Academy_Awards,Rental_Date, Return_Date, Cust_Name,
  3                        Cust_Street, Cust_ZipCode, Cust_Phone, Taxes, Fees, Damages, Discounts)
  4  VALUES (48944,
  5          5,
  6          'DVD_HFigures1',
  7          48944101,
  8          'HIDDEN_FIGURES',
  9          'Taraji P. Henson, Octavia Spencer, Janelle Monáe, Kevin Costner, Kirsten Dunst, Jim Parsons',
 10          127,
 11          'BIOGRAPHY/DRAMA',
 12          'PG',
 13          2016,
 14          'Theodore Melfi',
 15          'Best Adapted Screenplay, Best Picture, and Best Supporting Actress - Academy_Awards_2016',
 16          '20/jul/18',
 17          '20/jul/21',
 18          'Taraji Istaken',
 19          '4 Myempire Place',
 20          23232,
 21          9876543210,
 22          0.49,
 23          0,
 24          0,
 25          1.00);

1 row created.

SQL> select cust_name from rentals;

CUST_NAME                                                                       
------------------------------                                                  
Susie Newbie                                                                    
John DaMan                                                                      
Ralpheez MadeUp                                                                 
Teresa Ishername                                                                
Taraji Istaken                                                                  

SQL> select cust_name from storehub;

CUST_NAME                                                                       
------------------------------                                                  
Susie Newbie                                                                    
John DaMan                                                                      
Ralpheez MadeUp                                                                 
Teresa Ishername                                                                
Taraji Istaken                                                                  

SQL> select cust_name from customers;

CUST_NAME                                                                       
------------------------------                                                  
John DaMan                                                                      
Ralpheez MadeUp                                                                 
Susie Newbie                                                                    
Taraji Istaken                                                                  
Teresa Ishername                                                                

SQL> DELETE FROM STOREHUB WHERE Cust_Name = 'John DaMan';

1 row deleted.

SQL> select cust_name from storehub;

CUST_NAME                                                                       
------------------------------                                                  
Susie Newbie                                                                    
Ralpheez MadeUp                                                                 
Teresa Ishername                                                                
Taraji Istaken                                                                  

SQL> spool off
