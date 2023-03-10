# ANN-in-R
#In this project I have used NNET library to create ANN in R.
#####Codes Used###############

library(nnet)
iris<-read.csv("/Users/nirajkc/Downloads/archive (4)/iris.csv")
data(iris)
head(iris)
summary(iris)

# fit model
fit <- nnet(Species~., data=iris, size=4, decay=0.0001, maxit=500)
# summarize the fit
summary(fit)
# make predictions
predictions <- predict(fit, iris[,1:4], type="class")
# summarize accuracy
library(caret)
predictions <- factor(predictions, levels = levels(iris$Species))
confusionMatrix(predictions, iris$Species)
