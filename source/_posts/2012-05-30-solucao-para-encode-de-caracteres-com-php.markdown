---
layout: post
title: "Solução para encode de caracteres com PHP"
date: 2012-05-30 22:50
comments: true
categories: [php, dicas]
---



<h2>O Problema</h2>
<p>
Tratar de caracteres sempre é um problema quando se diz respeito ao encode. 
Em algumas situações, somos remetidos a lidar com dados de bases diferentes onde o encode também é diferente, porém precisamos trata-los igualmente, seja para apresentação, persistência ou qualquer outra finalidade.
</p>

É ideal que entendamos o funcionamento a tabela de encodes, para isso segue uma artigo interessantíssimo feita pelo site Tableless: <a href="http://tableless.com.br/charsets-e-encodes-tabelas-de-caracteres/">Entenda como funciona a tabela de caracteres e encodes no HTML</a>.
</p>


<h2>Certo, mas e a solução?</h2> 
<p>
Bem, escrevi uma função hà um tempo atrás para resolver justamente este tipo de problema. 
Desta forma, temos uma função capaz de encodar objetos sejam eles classes, arrays ou strings.

{% codeblock charset_transfer.php lang:php %}
<?php
/**
 * Funcao para encodar/decodar (charset) texto.
 * Suporta array multidimensional
 *
 * @author kenshin6x <seisxis@gmail.com>
 *
 * @param mixed $input Valor a ser encodado/decodado. Caso seja um objeto, é necessario que seus atributos sejam publicos, e neste caso, o retorno sera uma copia do objeto, mantendo nome e atributos
 * @param string $function Nome da funcao a ser usada para transferir.
 *
 * @return mixed $return
 */

function charset_transfer($input,$function) {
    switch(gettype($input)) {
        case "string":
            $return = call_user_func($function,$input);
        break;
        
        case "array":
            foreach ($input as $key => $val) {
                if(is_string($val)) {
                    $return[$key] = call_user_func($function,$val);
                } else {
                    $returnTemp = charset_transfer($val,$function);
                    $return[$key] = $returnTemp;
                }
            }
        break;  
        
        case "object":
            $inputVars = get_object_vars($input);
            $className = get_class($input);
            $classInstance = new $className();
            
            foreach ($inputVars as $key => $val) {
                if(is_string($val)) {
                    $classInstance->$key = call_user_func($function,$val);
                } else {
                    $returnTemp = charset_transfer($val,$function);
                    $classInstance->$key = $returnTemp;
                }
            }
            
            return $classInstance;
            
        break;
        
        default:
            die("charset_transfer ERROR: TYPE UNSUPPORTED");
    }
    
    return $return;
}
?>

{% endcodeblock %}
</p>