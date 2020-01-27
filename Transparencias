public void paintTransparentImage(Matrix2D image, int x, int y) {
        if (matrix != null || image != null || x <= matrix.getWeight() || y <= matrix.getHeight() || x >= 0 || y >= 0) {
            for (int i = 0; i < image.getHeight(); i++) {
                for (int j = 0; j < image.getWeight(); j++) {
                    int xd = (int) (j + x);
                    int yd = (int) (i + y);
                    int color_background = matrix.getValue(xd, yd);
                    int color_foreground = image.getValue(j, i);
                    int alpha = getAlphaChannel(color_foreground);
                    int final_color = interpolar(color_foreground, color_background, alpha / 255.0);
                    matrix.setValue(xd, yd, final_color);
                }
            }
        }
    }

    public static int getAlphaChannel(int color) {
        int colorA = (color >> ALPHA_DISPLACEMENT) & 255;
        return colorA;
    }

    public static int interpolar(int color, int color2, double medium) {

        int colorA = (color >> ALPHA_DISPLACEMENT) & 255;
        int colorR = (color >> RED_DISPLACEMENT) & 255;
        int colorG = (color >> GREEN_DISPLACEMENT) & 255;
        int colorB = (color >> BLUE_DISPLACEMENT) & 255;

        int colorBA = (color2 >> ALPHA_DISPLACEMENT) & 255;
        int colorBR = (color2 >> RED_DISPLACEMENT) & 255;
        int colorBG = (color2 >> GREEN_DISPLACEMENT) & 255;
        int colorBB = (color2 >> BLUE_DISPLACEMENT) & 255;

        double alpha = colorBA * (1 - medium) + colorA * medium;
        double red = colorBR * (1 - medium) + colorR * medium;
        double green = colorBG * (1 - medium) + colorG * medium;
        double blue = colorBB * (1 - medium) + colorB * medium;

        int finalColor = (int) alpha << ALPHA_DISPLACEMENT | (int) red << RED_DISPLACEMENT | (int) green << GREEN_DISPLACEMENT | (int) blue << BLUE_DISPLACEMENT;
        return finalColor;

    }
