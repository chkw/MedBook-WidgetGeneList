# SEPT 2015 chrisw
# Package up word cloud scripts into one file.

BOWER_DIR = ../../bower_components

SCRIPTS_DEPS = $(BOWER_DIR)/jquery/dist/jquery.js $(BOWER_DIR)/select2/dist/js/select2.js geneList.js
SCRIPTS = geneList.js

TARGETS = geneList_plugin.js

CLOSURE_COMPILER_JAR = ~/git/closure-compiler/build/compiler.jar
#COMPILATION_LEVEL = WHITESPACE_ONLY
COMPILATION_LEVEL = SIMPLE_OPTIMIZATIONS
#COMPILATION_LEVEL = ADVANCED_OPTIMIZATIONS

METEOR_PACKAGE_DIR = ~/workspace/MedBook-Packages/select2genelist

test:

bower_update:
	bower update ;
	\

bower_clean:
	rm -rf $(BOWER_DIR) ;
	\

sync_meteor: geneList_plugin_dev.js
	rsync -avP $< $(METEOR_PACKAGE_DIR)/geneList_plugin_dev.js;
	\

geneList_plugin.js: $(SCRIPTS)
	java -jar $(CLOSURE_COMPILER_JAR) --compilation_level $(COMPILATION_LEVEL) --js_output_file=$@ $(SCRIPTS) ;
	\

geneList_plugin_deps.js: $(SCRIPTS_DEPS)
	rm -f 1.tmp ;
	\
	for script in $(SCRIPTS_DEPS) ; do \
		cat $$script >> 1.tmp ; \
	done ;
	\
	mv 1.tmp $@ ;
	\
	rm -f 1.tmp ;
	\

geneList_plugin_dev.js: $(SCRIPTS)
	rm -f 1.tmp ;
	\
	for script in $(SCRIPTS) ; do \
		cat $$script >> 1.tmp ; \
	done ;
	\
	mv 1.tmp $@ ;
	\
	rm -f 1.tmp ;
	\

clean:
	rm -f $(TARGETS)
