# How to use modelviewerloader with modelviewer

1. <strong>Clone or fork this repository</strong>

2. <strong>Generate a personal access token.</strong> It is recommended to use a fine-grained token with permissions set to only read/write the modelviewerloader repository. You can generate the token [here](https://github.com/settings/apps)

3. <strong>Provide your Github username and generated token</strong> inside both the modelviewerloader and modelviewer applications

You can either host the Model Viewer Loader yourself (e.g., using GitHub Pages) or access it [here](https://modelviewerloader.netlify.app/)
<br/>
Model Viewer application can be downloaded [here](https://github.com/Fuyutami/modelviewer)
<br/>

# How to Prepare an AutoCAD Project for Import into Model Viewer

1. **Set AutoCAD Units Correctly:**  
   Ensure that the units in AutoCAD are properly set. In the example below, if you want the model to have a width of 1 meter in Model Viewer, the Insertion Scale in AutoCAD should be set to millimeters.
   
   ![alt text](https://raw.githubusercontent.com/Fuyutami/modelviewerloader/master/demo/guide1.png)


3. **Convert 3D Models to Mesh Objects:**  
   All 3D models must be converted to mesh objects using the `MESHOPTIONS` command.

   ![alt text](https://raw.githubusercontent.com/Fuyutami/modelviewerloader/master/demo/guide2.png)
  
   - Set the mesh type to **Triangle** for optimal results.
      - **WARNING:** Quads are fine (Model Viewer can triangulate them), but **NGONS MUST NOT BE USED**.  
   - Adjust the **Mesh distance from original faces** setting to reduce file size.
     - **WARNING:** Do not try to make the mesh appear smooth in AutoCAD by setting this parameter too small, as this will unnecessarily increase the polygon count and result in a much larger file size.  
     - In the example below, a value of **5 units** is used for this distance, which works well for this particular model. Visible polygons on bevels will be automatically smoothed in Model Viewer.
    
     ![alt text](https://raw.githubusercontent.com/Fuyutami/modelviewerloader/master/demo/guide3.png)
        
     - **Note:** This value may need to be adjusted depending on the model size, as it will not work the same for every model.

   

5. **Export the Model:**  
   Once the model is ready, export it as a DXF file. It is recommended to use **AutoCAD 2018 DXF**, though other DXF formats from the list should work as well.

   ![alt text](https://raw.githubusercontent.com/Fuyutami/modelviewerloader/master/demo/guide4.png)


# Model Viewer F.A.Q.
1.  **Model not visible after loading?** <br/>
Ensure your Wi-Fi connection is stable and all project geometry in AutoCAD is converted to MESH.<br/>
2.  **Model scale or location incorrect?** <br/>
Verify that units are set correctly in AutoCAD.
3.  **Is the model taking too long to load?** <br/>
To improve loading times, try reducing the size of your DXF file. When converting objects to MESH in AutoCAD using the MESHOPTIONS command, aim to decrease the polygon count. This will help the model load faster. Keep in mind that loading speed can also be affected by your Wi-Fi connection.
