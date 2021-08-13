.. index::
   single: SASS;

SASS
===================

   $base-color: #c6538c;
   $border-dark: rgba($base-color, 0.88);

   .alert {
   border: 1px solid $border-dark;
   }

Operation
===================


    == and != are used to check if two values are the same.
    +, -, *, /, and % have their usual mathematical meaning for numbers, with special behaviors for units that matches the use of units in scientific math.
    <, <=, >, and >= check whether two numbers are greater or less than one another.
    and, or, and not have the usual boolean behavior. Sass considers every value “true” except for false and null.
    +, -, and / can be used to concatenate strings.
    ( and ) can be used to explicitly control the precedence order of operations.
