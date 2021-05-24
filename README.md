# plugin-samples
IDE Plugin Samples

Samples of custom worksheets for the Uniface 10.3 IDE, similar to those included in <https://community.uniface.com/display/DOW/Uniface+10.3+IDE+Utilities>.

They can be used to explore how IDE add-ins work, or as a basis for adding features or building your own. See the [documentation](https://documentation.uniface.com/10/uniface/ide/customizingIDE/ideWorksheetPlugin/aboutWorksheetPlugIns.htm?tocpath=Managing%20Development%7CIDE%20Worksheet%20Plug-Ins%7C_____0)
 for more information on the IDE Worksheet Plugin API. 
 
## Contents

The supplied plugins currently include the following:
- View Listing
- Checkstyle
- View Statistics

### View Listing (WS_LISTING)

- Shows component compilation listings in an additional tab.
- A rich text edit box is used to display the listing, so search functionality (Ctrl F) is available.

### Checkstyle (WS_CHECKSTYLE)

- Analyzes code and reports standards contraventions.
- The supplied code performs basic changes that entries start with *l* for local proc. You can also check operation names (e.g. *op* prefix) in a similar manner (not enabled by default). The logical assignments **WS_CHECKSTYLE_ENTRY_PREFIX** and **WS_CHECKSTYLE_OPERATION_PREFIX** can be used to change the prefixes used, or you can modify the defaults and script in **operation analyzeCode**
    
### View Statitics (WS_STATISTICS)

- Analyzes and reports lines of code in your component

## Dependencies

- Uses the Uniface meta dictionary (uniface\misc\umeta.xml in the Uniface installation), which is included in the versioned code.
- The Uniface WASListener is required to import WorkArea export files into the repository database and subsequently synchronize them: https://github.com/uniface/WASListener

## Notes

**Warning:** Do not import this version into a Uniface environment other than version 10.3, as the Uniface meta dictionary will differ. Check git branches for your version.

## Development Environment Installation and Configuration

1. The supplied shortcuts assume a default Uniface 10 Community Edition install in **C:\Program Files (x86)\Uniface 10 Community Edition**. If your Uniface installation differs, edit the shortcuts and change the Uniface installation location (don't forget to change the **/adm** switch as well) and working folder if needed.
2. Edit your assignment file specified in your shortcut with the **/asn** switch (e.g. **.\asn\ide.asn**) if needed.
   Paths to related files are relative to the shortcut working folder, and the supplied assignment file assumes that the WASListener is installed in the Uniface installation folder. If this is not the case, then you will need to change the assignment file accordingly.
3. Start the IDE and load the default templates using the supplied shortcut.
4. From the main menu select **Import WorkArea** to import the source code export files into your repository.
5. To resolve messages about being unable to find the resources for the plugins within the development environment, Compile the **PLUGIN_SAMPLES** project using the build shortcut to populate the **reources** folder and close the IDE.
6. Using the Build shortcut, type **/all** at the command line to compile **PLUGIN-SAMPLES.uar**.

## Configuration for use

- Modify the assignment file of your target development environment (e.g. IDE.asn) as follows:

  - Add **PLUGIN-SAMPLES.uar** to the **\[RESOURCES\]** section, modifying the location as needed. Note: to avoid odd behavior, add the **RESOURCES** section at the top of your assignment file before including other assignment files with #file:

        [RESOURCES]
        ..\plugin-samples\PLUGIN-SAMPLES.uar

  - Add or modify **[LOGICALS]** to include the desired plug-ins:

        [LOGICALS]
        IDE_DEFINE_WORKSHEETS = WS_LISTING,WS_STATISTICS,WS_CHECKSTYLE

## Licence

MIT
