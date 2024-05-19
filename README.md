# Task-2-express-js
//   CategoryController.js

//Function = getAllCategory

const getAllCategory=async (req,res)=>{
    try{
        const category= await Category.find();
        return res.json({category});
    }catch(err){
        return res.json({error : err});
    };
};

// Function = getCategoryById

const getCategorybyId=async (req,res)=>{
    console.log(req.params);
    const categoryId = (req.params.Id);
    try{
        const category =await Category.findOne({_id: categoryId});
        return res.json({data:category});
    }catch(err){
        return res.json({error:err});
    };
};


module.exports ={
     getAllCategory,
     getCategorybyId,
};     




//   CategoryRoutes.js

const express=require("express");
const { getAllCategory, getCategorybyId}=require("../../Controllers/Category/CategoryController");

const categoryRouter = express.Router();

categoryRouter.get("/all-category", getAllCategory );
categoryRouter.get("/category-by-id/:Id",getCategorybyId);

module.exports=categoryRouter;
