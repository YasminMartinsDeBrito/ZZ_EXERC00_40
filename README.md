REPORT ZZ_EXERC01_40.

DATA : v_rua          TYPE string,
       v_media        TYPE i,
       v_contador     TYPE i,
       v_preco        TYPE netpr,
       v_area         TYPE i,
       v_opcao        TYPE string,
       v_telefone(11) TYPE c.


------------------------------------------------------
REPORT zz_exerc02_00.

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
