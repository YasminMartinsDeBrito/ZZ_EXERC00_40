REPORT ZZ_EXERC01_40.

DATA : v_rua          TYPE string,
       v_media        TYPE i,
       v_contador     TYPE i,
       v_preco        TYPE netpr,
       v_area         TYPE i,
       v_opcao        TYPE string,
       v_telefone(11) TYPE c.


------------------------------------------------------
REPORT zz_exerc02_40.

CONSTANTS: c_valuea TYPE i VALUE 3,
           c_valueb TYPE i VALUE 2,
           c_valuec TYPE i VALUE 5.

DATA: v_result TYPE char11.


START-OF-SELECTION.

*A
  IF c_valuea > c_valueb.
    v_result = 'Verdadeiro'.
  ELSE.
    v_result = 'Falso'.
  ENDIF.
  PERFORM f_exibe_msg.

*B
  IF c_valueb = c_valuea.
    v_result = 'Verdadeiro'.
  ELSE.
    v_result = 'Falso'.
  ENDIF.
  PERFORM f_exibe_msg.

*C
  IF c_valuea >= c_valueb AND c_valuec <> 5.
    v_result = 'Verdadeiro'.
  ELSE.
    v_result = 'Falso'.
  ENDIF.
  PERFORM f_exibe_msg.

*D
  IF c_valueb < c_valuea OR c_valuea = 3.
    v_result = 'Verdadeiro'.
  ELSE.
    v_result = 'Falso'.
  ENDIF.
  PERFORM f_exibe_msg.

*E
  IF c_valuea > c_valueb OR c_valuea = 3.
    v_result = 'Verdadeiro'.
  ELSE.
    v_result = 'Falso'.
  ENDIF.
  PERFORM f_exibe_msg.

*F
  IF c_valuec <= 7 AND c_valueb > 0 AND c_valuec > c_valuea.
    v_result = 'Verdadeiro'.
  ELSE.
    v_result = 'Falso'.
  ENDIF.
  PERFORM f_exibe_msg.



FORM f_exibe_msg.
  MESSAGE i001(z00_y) WITH v_result.
ENDFORM.

----------------------------------------------------------------
REPORT ZZ_EXERC03_40.

data: area type p.

parameters: p_altura type p,
            p_base type p.

START-OF-SELECTION.

area = ( p_altura * p_base ) / 2.

perform  f_exibe_msg.




FORM f_exibe_msg .
  message i002(z00_y) with area.
ENDFORM.



----------------------------------------------------------

REPORT ZZ_EXERC04_40.

data: v_media type p decimals 2.

parameters:  p_nota1 type p decimals 2,
             p_nota2 type p decimals 2,
             p_nota3 type p decimals 2,
             p_nota4 type p decimals 2.


START-OF-SELECTION.


perform f_media using p_nota1 p_nota2 p_nota3 p_nota4.
perform f_msg.

FORM f_media using   ip_nota1
                     ip_nota2
                     ip_nota3
                     ip_nota4.
  v_media = ( ip_nota1 + ip_nota2 + ip_nota3 + ip_nota4 ) / 4.


ENDFORM.
FORM f_msg .
  message i003(z00_y) with v_media.
ENDFORM.


----------------------------------------------------------------



REPORT zz_exerc05_40.

DATA: v_idade TYPE p DECIMALS 2,
      v_2015  TYPE p DECIMALS 2.

PARAMETERS: p_nasc  TYPE char4 OBLIGATORY,
            p_atual TYPE char4 OBLIGATORY.

CONSTANTS: c_2015 TYPE p VALUE 2015.


START-OF-SELECTION.

  PERFORM f_calc_idade.
  PERFORM f_msg_idade.
  PERFORM f_calc_2015.

FORM f_calc_2015.
  IF p_nasc <= c_2015.
    v_2015 = c_2015 - p_nasc.
    PERFORM f_msg_2015.
  ENDIF.
ENDFORM.


FORM f_calc_idade.
  v_idade = p_atual - p_nasc.
ENDFORM.



FORM f_msg_idade .
  MESSAGE i004(z00_y) WITH v_idade.
ENDFORM.



FORM f_msg_2015.
  MESSAGE i005(z00_y) WITH v_2015.
ENDFORM.

-------------------------------------------------------

REPORT zz_exerc06_40.


PARAMETERS: p_value TYPE p DECIMALS 2.

CONSTANTS: c_number TYPE p VALUE 3.

START-OF-SELECTION.

PERFORM f_number.

FORM f_number.
	IF p_value <= c_number.
		MESSAGE i000(z00_y) WITH p_value.
	ELSE.
		MESSAGE i000(z00_y) WITH 'Hey Man,o numero é maior que 'c_number.
	ENDIF.
ENDFORM.

----------------------------------------------------------------------------


REPORT zz_exerc07_40.

DATA: v_result TYPE i.

PARAMETERS: p_num1 TYPE i,
            p_num2 TYPE i.


START-OF-SELECTION.

  PERFORM f_number_maior.
  PERFORM f_msg.


FORM f_number_maior .
  IF p_num1 >= p_num2.
    v_result = p_num1.
  ELSE.
    v_result = p_num2.
  ENDIF.
ENDFORM.



FORM f_msg .
  MESSAGE i000(z00_y) WITH 'O numero maior é'v_result.
ENDFORM.



----------------------------------------------------------------

REPORT zz_exerc08_40.

DATA: v_result TYPE c.

PARAMETERS: p_number TYPE i.

START-OF-SELECTION.

  PERFORM f_verif_number.


FORM f_verif_number .
  IF p_number MOD 2 = 0.
    v_result = 'O numero é PAR'.
  ELSE.
    v_result = 'O numero é IMPAR'.
  ENDIF.
  PERFORM f_msg.
ENDFORM.


FORM f_msg.
  MESSAGE i000(z00_y) WITH v_result.
ENDFORM.

----------------------------------------------------------------

REPORT zz_exerc09_40.

PARAMETERS:p_altura TYPE p DECIMALS 2 OBLIGATORY,
           p_sexo   TYPE char1 OBLIGATORY.

DATA: v_calculo     TYPE p DECIMALS 2,
      v_peso_homem  TYPE p DECIMALS 2 VALUE '72.7',
      v_peso_mulher TYPE p DECIMALS 2 VALUE '62.1'.

CONSTANTS: v_sexo_mulher TYPE c VALUE 'F',
           v_sexo_homem  TYPE c VALUE 'M'.




START-OF-SELECTION.

  PERFORM f_peso_ideal.


FORM f_peso_ideal .
  IF p_sexo = v_sexo_homem.
    v_calculo = ( v_peso_homem * p_altura ) - 58.
     PERFORM f_msg.

  ELSEIF p_sexo = v_sexo_mulher.
    v_calculo = ( v_peso_mulher * p_altura ) - 45.
     PERFORM f_msg.
  ELSE.
    MESSAGE i000(z00_y) WITH 'Eita Errado, Coloque M = Masculino ou F = Feminino'.
  ENDIF.


ENDFORM.


FORM f_msg .
  MESSAGE i000(z00_y) WITH 'O peso ideal é' v_calculo.
ENDFORM.

----------------------------------------------------------------

REPORT zz_exerc10_40.

PARAMETERS: p_prim  TYPE i,
            p_seg   TYPE i,
            p_opera TYPE c OBLIGATORY.

DATA: v_result TYPE p DECIMALS 2.



START-OF-SELECTION.

  SELECTION-SCREEN BEGIN OF LINE.

  SELECTION-SCREEN END OF  LINE.
  PERFORM f_calc_mais.
  perform f_msg.


FORM f_calc_mais .
  CASE p_opera.
    WHEN '+'.
      v_result = p_prim + p_seg.
    WHEN '-'.
      v_result = p_prim - p_seg.
    WHEN '/'.
      v_result = p_prim / p_seg.
    WHEN '*'.
      v_result = p_prim * p_seg.
  ENDCASE.
ENDFORM.


FORM f_msg .
  MESSAGE i001(z00_y) WITH v_result.
ENDFORM.

----------------------------------------------------------------


REPORT zz_exerc11_40.

data: v_count type i value 1.

while v_count <= 100.
  write: v_count.
  v_count = v_count + 1.
endwhile.

----------------------------------------------------------------

REPORT zz_exerc12_40.

PARAMETERS: p_value TYPE i.

DATA: v_multiplicar TYPE i VALUE 1,
      v_result      TYPE i.

while v_multiplicar <= 10.
  v_result = p_value * v_multiplicar.
  write:/ p_value, 'X' , v_multiplicar, '=', v_result.
  v_multiplicar = v_multiplicar + 1.

endwhile.

----------------------------------------------------------------

REPORT zz_exerc13_40.

PARAMETERS: p_value TYPE i.

DATA:v_sequenc TYPE i VALUE 1.

WHILE v_sequenc <= p_value.
  WRITE / v_sequenc.
  v_sequenc = v_sequenc * 2.
ENDWHILE.


----------------------------------------------------------------

REPORT zz_exerc14_40.

DATA: v_maior TYPE i,
      v_menor TYPE i,
      v_count TYPE i.

PARAMETERS: p_value1 TYPE i,
            p_value2 TYPE i.

IF p_value1 > p_value2.
  v_maior = p_value1.
  v_menor = p_value2.
ELSE.
  v_maior = p_value2.
  v_menor = p_value1.
ENDIF.

PERFORM f_results.



FORM f_menor_maior .
  WHILE v_count <= v_maior.
    WRITE v_count.
    v_count = v_count + 1.
  ENDWHILE.
ENDFORM.



FORM f_maior_menor .
  WHILE v_count >= v_menor.
    WRITE: v_count.
    v_count = v_count - 1.
  ENDWHILE.
ENDFORM.


FORM f_results .
  WRITE: /'Menor para o Maior'.
  PERFORM f_menor_maior.

  CLEAR v_count.
  v_count = v_maior.
  write:/.

  WRITE: /'Maior para o Menor'.
  PERFORM f_maior_menor.

ENDFORM.

----------------------------------------------------------------

REPORT zz_exerc15_40.

PARAMETERS: p_num1 TYPE i,
            p_num2 TYPE i,
            p_num3 TYPE i,
            p_num4 TYPE i,
            p_num5 TYPE i.

DATA:  v_menor     TYPE i,
       v_maior     TYPE i,
       v_number    TYPE i,
       v_soma      TYPE i,
       v_media     TYPE p DECIMALS 2,
       v_media_par TYPE p DECIMALS 2.


v_media = ( p_num1 + p_num2 + p_num3 + p_num4 + p_num5 ) / 5.
v_soma =  p_num1 + p_num2 + p_num3 + p_num4 + p_num5.

v_maior = nmax( val1 = p_num1
                val2 = p_num2
                val3 = p_num3
                val4 = p_num4
                val5 = p_num5
).

v_menor = nmin( val1 = p_num1
                val2 = p_num2
                val3 = p_num3
                val4 = p_num4
                val5 = p_num5
).

if p_num1 mod 2 = 0.
  v_media_par = v_media_par + p_num1.
  v_number = v_number + 1.
endif.

if p_num2 mod 2 = 0.
  v_media_par = v_media_par + p_num2.
  v_number = v_number + 1.
endif.

if p_num3 mod 2 = 0.
  v_media_par = v_media_par + p_num3.
  v_number = v_number + 1.
endif.

if p_num4 mod 2 = 0.
  v_media_par = v_media_par + p_num4.
  v_number = v_number + 1.
endif.

if p_num5 mod 2 = 0.
  v_media_par = v_media_par + p_num5.
  v_number = v_number + 1.
endif.

v_media_par = v_media_par / v_number.

write: /'Soma dos numeros: ', v_soma,
       /'Media dos numeros: ', v_media,
       /'Maior numero: ', v_maior,
       /'Menor numero: ', v_menor,
       /'Media dos numeros pares: ', v_media_par.

----------------------------------------------------------------

REPORT zz_exerc17_40.

DATA v_count TYPE i VALUE 100.

WHILE v_count <= 200.
  IF v_count MOD 1 <> 0 .
    WRITE v_count.
  ENDIF.
ENDWHILE.

----------------------------------------------------------------

REPORT zz_exerc18_40.

DATA: v_sala TYPE p DECIMALS 2.

PARAMETERS: p_hora  TYPE i,
            p_sal_h TYPE netpr.

IF p_hora > 160.
  v_sala = ( 160 * p_sal_h ) + ( ( p_hora - 160 ) * ( p_sal_h * '1.30' ) ).
ELSE.

  v_sala = p_hora * p_sal_h.
ENDIF.

WRITE: 'Seu Salário é: R$', v_sala.

----------------------------------------------------------------




