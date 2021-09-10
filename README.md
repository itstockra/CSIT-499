# CSIT-499

# Instructions for downloading ANTLR and running from terminal w/ UNIX
Prerequisits:
Before installing you will need java, the runtime enviornment and the development kit
Commands to install Java:
JDK: sudo apt install default-jdk
JRE: sudo apt install default-jdk

1. Create a directory for the install files, I'll use install_files for this example

2. CD into new directory
   cd /usr/local/install_files
   
3. Download antlr:
   wget https://www.antlr.org/download/antlr-4.9.2-complete.jar
   
4. Add antlr-4.9.2-complete.jar to CLASSPATH (add to .bashrc to permanently add to CLASSPATH)
   export CLASSPATH=".:/usr/local/install_files/antlr-4.9.2-complete.jar:$CLASSPATH"
   
5. Create aliases for using ANTLR tools (again, add to .bashrc for permanent aliases)
   alias antlr4='java -Xmx500M -cp "/usr/local/install_files/antlr-4.9-complete.jar:$CLASSPATH" org.antlr.v4.Tool'
   alias grun='java -Xmx500M -cp "/usr/local/install_files/antlr-4.9-complete.jar:$CLASSPATH" org.antlr.v4.gui.TestRig'

6. Download CPP14 grammar files from Github using links below
   Lexer: wget https://raw.githubusercontent.com/antlr/grammars-v4/master/cpp/CPP14Lexer.g4
   Parser: wget https://raw.githubusercontent.com/antlr/grammars-v4/master/cpp/CPP14Parser.g4

7. Run commands:
   antlr4 CPP14Lexer.g4
   antlr4 CPP14Parser.g4

8. Compile and build Java classes
   javac CPP14*.java

9. Use grun to parse cpp files and generate parse tree along with gui of parse tree
   grun CPP14 translationUnit -tree -gui "location_of_any_cpp_file" 
   
