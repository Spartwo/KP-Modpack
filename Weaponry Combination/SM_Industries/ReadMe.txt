Notes on use of SM_Industries only 1 copy of SMI is required per KSP game install, The SM_industries folder should be installed directly to your KSP GameData folder, do not add or remove anything to or from SM_Industries.
SMI forms the EN_US localisation dictionary for SM Armory, SM Marine, SM AFV's, LBP, SM Stryker ,SM OSTandT, SM Aviation, SM ASW, SM NED
SMI also supplies  the plugin that provides the PaintShop feature and creates distinct part categories for each (SMI) maunfacturer

Notes on Paintshop function
The included Paintshop feature allows you to change the color of a crafts individual parts with one click.  There are requirements that need to be met in order for the system to function. A part must have an SMtextureswitch2 module, these are best applied by Module Manager patch or patches. A part must have alternate textures available, for best results these should be the same format and size as the originally used texture.
A patch example is provided below


//@PART[YOUR PART]:NEEDS[SMIndustries]
//{
//MODULE
//	{
//		 name = SMtextureswitch2
//		moduleID = 0
//		objectNames = Your parts object name, may not be the same as part name, check .MU with notepad++
//		textureNames = TheModFolder/Parts/ThePart/TheTexture;
//		textureDisplayNames = 0;  the texture name shown on the PAW
//		nextButtonText = Next Color
//		prevButtonText = Previous Color
//		statusText = Current Color
///		showPreviousButton = true
//		updateSymmetry = true
//		showInfo = false
//		debugMode = true
//		// //show or hide the List Objects button. Disabled by default. Should only be on while developing the part. //      Outputs a list of gameObjects in the part to the Alt+F2 log//
//		showListButton = true
//	}

For incredible results all parts should have been given matching textures or come from the same texture sheet, and all parts should be referenced in the patch in EXACTLY the same order for all parts 
A good example of this working are the AFV's and certain craft from SM marine