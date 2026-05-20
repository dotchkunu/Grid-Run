This is a Grid run and made by kunal (@dotchkunal)
*/
precision highp float;
out vec4 O;
uniform float time;
uniform vec2 resolution;
uniform vec2 move;
uniform vec2 wheel;
#define FC gl_FragCoord.xy
#define R resolution
#define T (time+113.+.2*wheel.y/MN)
#define S smoothstep
#define N normalize
#define MN min(R.x,R.y)
#define hue(a) (.5+.5*sin(3.14*(a)+vec3(1,2,3)))
#define LP vec3(1.+1.*sin(-T),2.-2.*cos(T),-3.-4.*sin(sin(T)))
vec3 render(vec2 uv);
void main() { O=vec4(render((FC-.5*R)/MN),1); } 
float smin(float a, float b, float k) {
	k*=log(2.);
	float x=b-a;
	return a+x/(1.-exp2(x/k));
