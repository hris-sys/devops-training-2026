# Stage 1: Build stage
FROM nginx:1.28-alpine AS builder
LABEL maintainer="hristian893@example.com"
WORKDIR /build
COPY index.html .

# Stage 2: Production stage
FROM nginx:1.28-alpine
LABEL description="DevOps Training Demo Application"

# Copy from builder stage
COPY --from=builder /build/index.html /usr/share/nginx/html/index.html

# Add health check
HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget --quiet --tries=1 --spider http://localhost/ || exit 1

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
