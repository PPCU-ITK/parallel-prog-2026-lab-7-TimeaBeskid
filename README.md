# assignment-7
module load nvhpc

module load cuda

module load craype-accel-nvidia80

nvc++ -mp=gpu -gpu=cc80 -Ofast laplace2d.cpp -o laplace -Minfo=accel,mp

srun -p gpu --gres=gpu:1 --ntasks=1 --time=00:05:00 --mem=40G ./laplace

