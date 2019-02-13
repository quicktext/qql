# The Lexical Anaylsis

| Name   |      Value      |
|----------|:-------------:|
| SPACE |  [ \r\n\t\b] + |
| COMMENT_INPUT |    '/*' .*? '*/'   |
| LINE_COMMENT | (('-- ' \| '#' \| '//') ~ [\r\n]* ('\r'? '\n' \| EOF) \| '--' ('\r'? '\n' \| EOF))  |
| COMMAND_ASSIGN | '=' |
| LR_BRACKET | '(' |
| RR_BRACKET | ')' |
| LS_BRACKET | '[' |
| RS_BRACKET | ']' |
| SEMI | ';' |
| COMMA | ',' |
| DOT | '.' |
| STAR | '*' |
| DIVIDE | '/' |
| MODULE | '%' |
| DQUOTE | '"' |
| SQUOTE | '\'' |
| VACUUM | V A C U U M |
| DELETE | D E L E T E |
| CLEAN | C L E A N |
| SELECT | S E L E C T |
| FROM | F R O M |
| WHERE | W H E R E |
| KEYWORD | K E Y W O R D  |
| WHEN | W H E N |
| CRON | C R O N |
| LIMIT | L I M I T |
| UPDATE | U P D A T E |
| UPDATE_LAZY | L A Z Y |
| UPDATE_LOCAL | L O C A L |
| UPDATE_REMOTE | R E M O T E |
| DO | D O |
| SORT | S O R T |
| ASC | A S C |
| DESC | D E S C |
| FILTER | F I L T E R |
| BLACK | B L A C K |
| WITH | W I T H |
| PLUGINS | P L U G I N S |
| WHICH | W H I C H |
| SCHEMA | S C H E M A |
| MODEL | M O D E L |
| CORPUS | C O R P U S |
| PLUGIN | P L U G I N |
| DAEMON | D A E M O N |
| LICENSE | L I C E N S E |
| fragment ID_LETTER | [a-zA-Z_] |
| fragment SQUOTA_STRING | '\'' ('\\' . \| '\'\'' \| ~ ('\'' \| '\\'))* '\'' |
| fragment DIGIT | [0-9]; |
| ID | ID_LETTER (ID_LETTER \| DIGIT)* |
| STRING_LITERAL | SQUOTA_STRING |
| NUMBEG_LITERAL | DIGIT + |
